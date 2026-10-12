# Resumen

Modo Playa Platform documenta un producto de alojamientos distribuido en tres repositorios; no agrega un servicio runtime.

- `modo-playa-app`: catálogo público Angular 20 / Ionic 8 para web y Android con Capacitor. Administra descubrimiento, contexto de destinos y favoritos locales.
- `modo-playa-admin`: operaciones autenticadas Angular 21 / Ionic 8 para alojamientos, disponibilidad, contactos, dashboard, usuarios y perfil.
- `modo-playa-api`: backend multi-tenant NestJS 11 con MongoDB, JWT, Resend, R2 y Sharp. Administra reglas por tenant, visibilidad pública y procesamiento de media.

## Base actual

Ambos clientes consumen la API. El admin ya adoptó multipart exclusivo hacia el backend, códigos de error de dominio y ownership explícito de soporte. La visibilidad pública admite documentos legacy sin el campo de visibilidad. Los destinos incluyen puntos de interés curados, clima cacheado y datos solares.

El deploy de la API migró a imágenes GHCR por SHA y OIDC/SSM en EC2 compartido. Los pendientes se concentran en validar soporte, estados de uploads y nombres legacy, sin inventar nuevos contratos backend. [Arquitectura](02-architecture.es.md), [roadmap](03-roadmap.es.md), [evidencia](04-evidence.es.md).

[English](01-overview.md).
