# Overview

Modo Playa Platform is a three-repository lodging system built around an operational distinction: what guests can discover publicly is not the same thing as what owners and administrators need to manage privately.

That is why the platform is split into a public catalog, an admin workspace, and a backend that owns shared rules, permissions, and file workflows. The goal is not just technical separation, but a cleaner product model.

## Components

- Public catalog frontend: destination browsing, lodging discovery, and lightweight local state such as favorites.
- Admin frontend: dashboards, lodgings, contacts, users, profile, and authenticated operational flows.
- Backend API: auth, contacts, dashboard, destinations, lodgings, users, mail, and media services.
- Storage and processing: MongoDB for data persistence, Cloudflare R2 for object storage, and server-side media normalization.

## Why The Split Matters

The public frontend is optimized for browsing.
The admin frontend is optimized for day-to-day operations.
The backend is optimized for ownership of access control, tenant boundaries, and media workflows.

This creates more coordination overhead than a single app, but it keeps the product model honest: public discovery and private operations have different constraints.

## Data Model

At a high level, the platform handles:

- tenants and owner-scoped access boundaries
- lodging and destination entities exposed through public and private views
- users, contacts, and dashboard-related operational data
- media assets validated and normalized before being stored in object storage

The key modeling concern is tenancy: the same backend serves multiple access contexts with different visibility and permissions.
