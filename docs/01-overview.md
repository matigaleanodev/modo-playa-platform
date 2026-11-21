# Overview

[Español](01-overview.es.md)

The public app owns discovery, destination browsing and local favorites. The admin app owns lodging operations, availability, contacts, users and profile screens. Both clients use a single API contract.

The API enforces owner scope, decides what appears in the public catalog, and processes images. MongoDB holds product data, and Cloudflare R2 holds processed media.

[Architecture](02-architecture.md)
