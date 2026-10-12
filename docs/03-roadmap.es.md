# Roadmap

## Base entregada

Están implementados media multipart exclusiva hacia backend, `targetOwnerId` explícito, resolución frontend de errores de dominio y contratos de visibilidad pública. Las consultas públicas conservan compatibilidad legacy de visibilidad. La entrega de la API usa OIDC/SSM e imágenes por SHA. La documentación de plataforma reutiliza la vista Archify revisada del portfolio.

## Pendientes

- Validar OWNER y SUPERADMIN por separado de punta a punta, incluyendo altas para otro owner, media y aislamiento.
- Cerrar UI de uploads pendientes: expiración, limpieza y reintento; agregar cobertura puntual para esos estados y forms/dialogs complejos.
- Decidir cuándo retirar el alias legacy `contacs` y alinear referencias entre clientes.
- Mantener fixtures de contratos públicos y controles manuales de destinos/runtime alineados.
- Mantener convenciones documentadas de auth/session/storage y guías de smoke/recuperación. Un workflow configurado o un test existente no demuestra validación de producción.

[English](03-roadmap.md).
