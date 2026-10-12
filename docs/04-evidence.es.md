# Evidencia y alcance

Revisión documental del 12/10/2026. Se contrastaron código/documentación local y SHA de main consultados en GitHub. Los commits locales de controles de identidad se cotejaron con workflows actuales de main. Esta tarea no accedió a AWS, ejecutó despliegues ni validó flujos de usuarios en producción.

## Revisiones de main

- [modo-playa-app @ d4fabb41284f](https://github.com/matigaleanodev/modo-playa-app/tree/d4fabb41284fca72fd987d5431074a52d41888f2)
- [modo-playa-admin @ b5a4c7910a29](https://github.com/matigaleanodev/modo-playa-admin/tree/b5a4c7910a29e943861f6af809071c6f208c5760)
- [modo-playa-api @ 82970dd6b7f6](https://github.com/matigaleanodev/modo-playa-api/tree/82970dd6b7f6dc82cc794c9431460611503e48c3)

## Fuentes

- [modo-playa-api/src/lodgings/lodgings.service.ts](https://github.com/matigaleanodev/modo-playa-api/blob/82970dd6b7f6dc82cc794c9431460611503e48c3/src/lodgings/lodgings.service.ts)
- [modo-playa-api/.github/workflows/deploy.yml](https://github.com/matigaleanodev/modo-playa-api/blob/82970dd6b7f6dc82cc794c9431460611503e48c3/.github/workflows/deploy.yml)
- [modo-playa-admin/src/app/lodgings/services/lodging-images-admin.service.ts](https://github.com/matigaleanodev/modo-playa-admin/blob/b5a4c7910a29e943861f6af809071c6f208c5760/src/app/lodgings/services/lodging-images-admin.service.ts)
- [modo-playa-admin/.github/workflows/ci.yml](https://github.com/matigaleanodev/modo-playa-admin/blob/b5a4c7910a29e943861f6af809071c6f208c5760/.github/workflows/ci.yml)
- [modo-playa-app/.github/workflows/deploy-firebase.yml](https://github.com/matigaleanodev/modo-playa-app/blob/d4fabb41284fca72fd987d5431074a52d41888f2/.github/workflows/deploy-firebase.yml)
- [modo-playa-app/.github/workflows/deploy-android-google-play.yml](https://github.com/matigaleanodev/modo-playa-app/blob/d4fabb41284fca72fd987d5431074a52d41888f2/.github/workflows/deploy-android-google-play.yml)
- [portfolio/Docs/product-architecture-evidence.es.md](https://github.com/matigaleanodev/portfolio/blob/34856adee211f57ddb32a8573b9af9578d73235b/Docs/product-architecture-evidence.es.md)
- [Workspace: AWS 2026-10-11](https://github.com/matigaleanodev/workspace/blob/2d808eb/Docs/operations/aws-access-2026-10-11.es.md)
- [Workspace: architecture](https://github.com/matigaleanodev/workspace/blob/2d808eb/Docs/architecture.es.md)

## Límites y mantenimiento

Los reportes operativos del workspace son evidencia histórica fechada; no certifican el estado vivo actual. Los diagramas conservan las revisiones originales en manifest.json, anteriores a esta revisión de documentación. Se verificaron hashes de JSON/HTML/PNG, enlaces locales y ausencia de Mermaid; se inspeccionaron visualmente ambas vistas previas. No se regeneraron diagramas ni se repitieron pruebas de las aplicaciones.

[English](04-evidence.md).
