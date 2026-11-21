# Arquitectura

[English](02-architecture.md) · [Diagrama del sistema](../README.es.md#arquitectura)

## Clientes y alcance por propietario

El catálogo consulta alojamientos y destinos de forma anónima. El panel admin envía JWT. La API aplica el rol y el alcance por propietario. Cuando soporte opera en nombre de otro propietario, envía `targetOwnerId` donde lo exige el contrato. El catálogo incluye alojamientos visibles y registros anteriores al campo `isPubliclyVisible`, y excluye los ocultos explícitamente.

## JSON e imágenes

CloudFront selecciona un origen según la ruta y conserva el hostname de la API. Las rutas JSON llegan a API Gateway HTTP API y sus handlers Lambda. Las rutas de carga de imágenes llegan a una Lambda Web Function con runtime HTTP nativo. Así se conservan los límites multipart de 10 MiB para imágenes de alojamiento y 5 MiB para perfil.

La API valida las cargas, normaliza imágenes con Sharp y guarda el resultado en R2. En el alta de alojamientos, el cliente asocia cargas pendientes con `uploadSessionId` y `pendingImageIds`. El backend gestiona la expiración, la limpieza y los permisos de almacenamiento.

## Persistencia y recuperación

MongoDB guarda alojamientos y datos de propiedad. Resend envía correos de cuenta. Open-Meteo y Sunrise-Sunset aportan contexto de destinos. Los clientes y la API se entregan por separado. La implementación NestJS conserva el contrato de clientes y sirve como recuperación mediante el enrutamiento de entrada.
