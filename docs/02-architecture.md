# Architecture

[System overview and interactive viewer](../README.md#architecture).

## Requests and ownership

The public app uses anonymous lodging/destination endpoints. Favorites remain local; they are not a server-side account feature. Admin calls carry JWT and use private endpoints. The backend applies owner scoping; expanded SUPERADMIN access does not imply implicit owner switching. Creation on behalf of another owner sends `targetOwnerId` explicitly where required.

`isPubliclyVisible` controls catalog exposure. The public query includes visible documents and legacy records where the field is absent; explicitly hidden lodgings remain excluded. Public responses and private operational views remain distinct.

## Media

Clients send `multipart/form-data` only to the API, which validates images, normalizes them with Sharp and writes to R2. No client coordinates signed uploads or writes directly to the bucket.

Profile images use self-service `POST`/`DELETE /api/auth/me/profile-image`. Lodging creation uploads drafts to `POST /api/admin/lodging-image-uploads` and associates them on submit using `uploadSessionId` and `pendingImageIds`. Existing lodgings use the images subresource for upload/default/delete. Expiration, cleanup and storage ownership stay in the backend; frontend retry/TTL UX and support validation remain pending.

## Persistence and integrations

MongoDB is the system of record. R2 stores processed media. Resend sends activation/recovery email. Open-Meteo weather uses a 30-minute in-memory cache; sun data comes from Sunrise-Sunset. Points of interest are curated configuration, not a live places-search integration.

## Deployment and checks

Frontends deploy independently. The public app has Firebase web and Google Play Android workflows; admin Firebase hosting is configured, but the reviewed main snapshot has no equivalent deployment workflow.

The API builds a GHCR image tagged by SHA. GitHub OIDC assumes the deployment role; SSM runs an allowlisted deployment script on shared EC2, verifies the image and checks health. Cloudflare Tunnel routes to an unpublished internal Traefik entrypoint. The shared-runtime record reports public 80/443/22 ingress closed; this is dated configuration evidence, not a new host audit. New identity checks verify the expected AWS account and bound workflow execution time.

Smoke targets include `/api/health`, `/docs`, `/openapi.json`, `/api/destinations`, `/api/lodgings` and authenticated `/api/admin/media/health`. A successful health response alone does not validate owner isolation, support operations or media uploads.

## Tradeoffs and remaining debt

Separate clients clarify product ownership but require cross-repo checks. Backend-owned media keeps storage rules consistent but requires explicit pending-upload UI. Multi-tenancy centralizes authorization and demands separate owner/support validation. Legacy `contacs` naming/aliases remain; frontend adoption is already implemented, while residual operational checks remain open. [Evidence](04-evidence.md).

[Español](02-architecture.es.md).
