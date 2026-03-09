# Architecture

The system is composed of:

- `modo-playa-app`, the public catalog used for anonymous browsing and lodging discovery
- `modo-playa-admin`, the authenticated operational surface for owners and administrators
- `modo-playa-api`, the multi-tenant backend responsible for auth, owner-scoped rules, public and private endpoints, and media workflows

The backend is the architectural anchor. It centralizes business rules, data access, and file-processing responsibilities that should not be duplicated in clients.

## Infrastructure

Both frontends are independently deployable and consume the same backend. The backend is container-oriented and integrates with MongoDB, object storage, mail services, and image-processing tooling.

Cloudflare R2 is used for media storage. AWS is part of the wider cloud footprint, while the API remains the central integration point for operational services.

## Decisions

- Split public and admin experiences into separate frontends instead of a single mixed application.
- Keep multi-tenant rules, auth, and media validation in the backend.
- Use object storage for media workflows rather than storing binary assets directly in the database.
- Maintain a clear distinction between public endpoints and authenticated operational endpoints.

## Tradeoffs

- Separate frontends improve clarity and product focus, but increase release and maintenance overhead.
- Centralized backend media handling improves consistency and control, but makes upload flows more complex.
- Multi-tenant backend design scales better for shared logic, but raises complexity around authorization semantics.
- The architecture is mature, but unresolved naming debt and partially normalized admin roles still create friction.
