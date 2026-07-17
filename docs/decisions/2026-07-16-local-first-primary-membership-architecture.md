# Local-First Primary-Membership Architecture

Version date: 2026-07-16
Status: Accepted

## Decision

Use a public-safe common layer plus private primary-membership adapters.

Common docs define billing rules, charge types, operating principles, templates, validation guidance, and synthetic fixtures. Real group data lives in a private adapter rooted at `memberships/<group-id>/`.

## Rationale

The system should eventually be shareable as an app without exposing real member names, member IDs, statements, reports, payment details, or rollups. Keeping storage behind a port lets the same billing rules work with local files now and browser-local storage, private repos, or export/import bundles later.

## Consequences

- Common docs must stay role-based and public-safe.
- Real membership adapters are ignored by Git by default.
- Paths inside an adapter stay group-relative, such as `records/YYYY/YYYY-MM/report.md`.
- Future frontends should calculate locally and store private data in the user's browser, selected folder, private repo, or explicit export unless a separate opt-in adapter is designed.
