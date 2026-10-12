# Arquitectura

[Vista del sistema y visor interactivo](../README.es.md#arquitectura).

## Peticiones y ownership

La app pública consume endpoints anónimos de alojamientos/destinos. Los favoritos son locales; no son una función de cuenta en el servidor. El admin envía JWT y consume endpoints privados. El backend aplica el scope por owner; los permisos ampliados de SUPERADMIN no implican cambio de owner implícito. Las altas en nombre de otro owner envían `targetOwnerId` donde corresponde.

`isPubliclyVisible` controla la exposición en el catálogo. La consulta pública incluye documentos visibles y registros legacy sin ese campo; excluye los ocultos explícitamente. Las respuestas públicas y las vistas operativas privadas siguen separadas.

## Media

Los clientes envían `multipart/form-data` solo a la API, que valida imágenes, normaliza con Sharp y escribe en R2. Ningún cliente coordina signed uploads ni escribe directamente al bucket.

Las imágenes de perfil usan autoservicio `POST`/`DELETE /api/auth/me/profile-image`. El alta de alojamientos sube borradores a `POST /api/admin/lodging-image-uploads` y los asocia al guardar con `uploadSessionId` y `pendingImageIds`. Los alojamientos existentes usan el subrecurso de imágenes para subir/default/eliminar. Expiración, limpieza y ownership del storage quedan en el backend; siguen pendientes UX de reintento/TTL y validación de soporte.

## Persistencia e integraciones

MongoDB es la fuente de datos. R2 almacena media procesada. Resend envía correos de activación/recuperación. El clima Open-Meteo tiene caché en memoria de 30 minutos; los datos solares provienen de Sunrise-Sunset. Los puntos de interés son configuración curada, no una integración de búsqueda de lugares en vivo.

## Despliegue y controles

Los frontends se despliegan de forma independiente. La app pública tiene workflows Firebase web y Google Play Android; el admin configura hosting Firebase, pero el snapshot main revisado no tiene un workflow equivalente de despliegue.

La API genera una imagen GHCR por SHA. GitHub OIDC asume el rol de deploy; SSM ejecuta un script permitido en EC2 compartido, verifica la imagen y comprueba salud. Cloudflare Tunnel enruta a un entrypoint interno Traefik sin publicación en el host. El registro del runtime compartido informa cierre del ingreso público 80/443/22; es evidencia fechada de configuración, no una nueva auditoría del host. Los nuevos controles de identidad verifican la cuenta AWS esperada y acotan la duración del workflow.

Los smoke targets incluyen `/api/health`, `/docs`, `/openapi.json`, `/api/destinations`, `/api/lodgings` y `/api/admin/media/health` autenticado. Una respuesta de salud exitosa no valida aislamiento de owners, operaciones de soporte ni uploads.

## Costos y deuda restante

Separar clientes aclara responsabilidades pero exige controles entre repos. Media en backend mantiene reglas consistentes pero requiere UI explícita para uploads pendientes. Multi-tenancy centraliza autorización y exige validar owner/soporte por separado. Persisten nombres/aliases legacy `contacs`; la adopción frontend está implementada y quedan controles operativos residuales. [Evidencia](04-evidence.es.md).

[English](02-architecture.md).
