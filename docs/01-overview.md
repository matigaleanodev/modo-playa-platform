# Overview

Modo Playa Platform documents a lodging product spanning three repositories; it adds no runtime service.

- `modo-playa-app`: Angular 20 / Ionic 8 public catalog for web and Android through Capacitor. Lodging discovery, destination context and local favorites belong here.
- `modo-playa-admin`: Angular 21 / Ionic 8 authenticated operations for lodgings, availability, contacts, dashboard, users and profile.
- `modo-playa-api`: NestJS 11 multi-tenant backend with MongoDB, JWT, Resend, R2 and Sharp. It owns tenant rules, public visibility and media processing.

## Current baseline

Both clients consume the API. The admin already adopted backend-only multipart uploads, domain error codes and explicit support ownership. Public lodging visibility supports legacy documents without the visibility field. Destination context includes curated points of interest, cached weather and sun data.

The API deployment moved to GHCR images by SHA and OIDC/SSM on shared EC2. Remaining work concentrates on support-flow validation, upload states and legacy naming rather than inventing new backend contracts. [Architecture](02-architecture.md), [evidence](04-evidence.md).

[Español](01-overview.es.md).
