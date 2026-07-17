# Local-First Architecture

Version date: 2026-07-16
Last updated: 2026-07-16

## Purpose

The billing system has a public-safe core and private primary-membership adapters. The core defines Bay Club billing behavior. Adapters provide storage for real statements, profiles, reports, rosters, payments, and rollups.

## Layers

- Core domain: `docs/rules.md`, `docs/charge-types.md`, templates, validation guidance, and synthetic examples.
- Membership adapter: a private group root such as `memberships/<group-id>/` with `profile.md`, `records/`, `rollups/`, and `decisions/`.
- Storage port: the interface the future app uses to read and write profiles, statement files, monthly reports, CSV rows, rollups, decisions, and export bundles.
- Storage adapters: filesystem now; private repo, browser-local storage, and export/import bundles later.

## Storage Port Contract

A storage adapter must support these capabilities without changing billing rules:

- List available membership groups and select one active group.
- Read and update the selected group's profile.
- Store and retrieve source statements and extracted statement evidence.
- Store and retrieve monthly reports, charges CSVs, and payments CSVs.
- Store and retrieve per-group rollups.
- Store group-specific decision records.
- Export and import a portable membership packet.

Paths inside an adapter should stay group-relative, such as `records/2026/2026-04/report.md`, so a group can move from local filesystem to private repo or browser storage without rewriting its internal references.

## Privacy Defaults

Real billing data must stay local or user-owned by default. A hosted frontend should calculate in the browser and store private data in browser-local storage, a user-selected folder, a private repository, or an explicit export bundle.

Do not upload real statements, profiles, reports, payment details, or generated private outputs to an application server by default. Cloud sync, collaboration, analytics, or remote persistence must be explicit opt-in adapters with separate privacy decisions.

## Browser-Local Direction

The future frontend should be able to run without a hosted data backend. Use browser-local storage for private data:

- IndexedDB for structured profile, roster, charge, payment, and rollup records.
- OPFS or File System Access API for source statements and larger artifacts when available.
- Export/import bundles for portability and backup.

The app shell and billing logic can be public. Private membership data should remain in the user's chosen storage adapter.
