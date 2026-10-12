# Roadmap

## Delivered baseline

Backend-only multipart media, explicit `targetOwnerId`, frontend domain error mapping and public visibility contracts are implemented. Public queries retain legacy visibility compatibility. API delivery uses OIDC/SSM and SHA-tagged images. Platform documentation now reuses the reviewed portfolio Archify overview.

## Remaining work

- Validate OWNER and SUPERADMIN separately end to end, including creation for another owner, media and isolation boundaries.
- Close pending-upload UI for expiration, cleanup and retry; add focused coverage for these states and complex forms/dialogs.
- Decide when to remove the legacy `contacs` alias and align references across clients.
- Keep public-contract fixtures and destination/manual runtime checks aligned.
- Maintain documented auth/session/storage conventions and smoke/recovery guidance. A configured workflow or existing unit test does not establish production validation.

[Español](03-roadmap.es.md).
