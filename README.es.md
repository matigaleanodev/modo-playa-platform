# Modo Playa Platform

[🇬🇧 English](README.md) | [🇪🇸 Español](README.es.md)

Modo Playa Platform documenta el modelo operativo detrás del producto: un catálogo público de alojamientos, una superficie administrativa para dueños y operadores, y un backend multi-tenant que mantiene consistentes los permisos, las reglas de negocio y el manejo de media.

![Angular](https://img.shields.io/badge/Angular-Frontend-DD0031?style=flat-square&logo=angular&logoColor=white)
![NestJS](https://img.shields.io/badge/NestJS-Backend-E0234E?style=flat-square&logo=nestjs&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-Data-47A248?style=flat-square&logo=mongodb&logoColor=white)
![Cloudflare R2](https://img.shields.io/badge/Cloudflare_R2-Storage-F38020?style=flat-square&logo=cloudflare&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Deploy-2496ED?style=flat-square&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-Cloud-232F3E?style=flat-square&logo=amazonaws&logoColor=white)

## Repositorios de Código

- [`modo-playa-admin`](https://github.com/matigaleanodev/modo-playa-admin) -> panel de administracion Angular + Ionic
- [`modo-playa-api`](https://github.com/matigaleanodev/modo-playa-api) -> backend multi-tenant en NestJS
- [`modo-playa-app`](https://github.com/matigaleanodev/modo-playa-app) -> catalogo publico

## Por Qué Existe Este Repo

Este repositorio existe para explicar el producto como un sistema coordinado y no como tres aplicaciones aisladas.

La app pública, el panel admin y el backend resuelven problemas distintos. Este repo hace explícita esa separación: descubrimiento para huéspedes, operación para administradores y control compartido en el backend.

## Foco Actual

- preservar un límite claro entre navegación pública y operaciones autenticadas
- mantener centralizadas en el backend las reglas de tenant y permisos
- volver predecible el manejo de media en los flujos administrativos
- documentar la plataforma en términos de operación de producto, no solo de infraestructura

## Arquitectura

```mermaid
flowchart LR
  User --> PublicApp[modo-playa-app]
  AdminUser --> Admin[modo-playa-admin]
  PublicApp --> API[modo-playa-api]
  Admin --> API
  API --> DB[(MongoDB)]
  API --> R2[Cloudflare R2]
```

## Docs

- [Overview](docs/01-overview.md)
- [Architecture](docs/02-architecture.md)
- [Roadmap](docs/03-roadmap.md)
