# Architecture

[Español](02-architecture.es.md) · [System diagram](../README.md#architecture)

## Clients and ownership

The catalog reads public listings and destinations anonymously. The admin app sends JWTs. Authorization applies the caller's role and owner scope. Support acting for another owner sends `targetOwnerId` where the contract requires it. The public catalog includes visible listings and legacy records without `isPubliclyVisible`, and excludes explicitly hidden records.

## JSON and media

CloudFront selects an origin by path while preserving the API hostname. JSON routes go to API Gateway HTTP API and their Lambda handlers. Image upload routes go to a Lambda Web Function with a native HTTP runtime. This preserves the multipart limits of 10 MiB for lodging images and 5 MiB for profile images.

The API validates uploads, uses Sharp to normalize images, and writes processed media to R2. Lodging creation attaches pending uploads through `uploadSessionId` and `pendingImageIds`. The backend owns expiration, cleanup and storage authorization.

## Persistence and recovery

MongoDB holds listings and ownership data. Resend delivers account emails. Open-Meteo and Sunrise-Sunset provide destination context. The clients and API ship independently. The NestJS implementation preserves the same client-facing contract and remains available as a recovery path through ingress routing.
