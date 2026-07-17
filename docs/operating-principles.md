# Operating Principles

Version date: 2026-07-15
Last updated: 2026-07-16

## Purpose

These principles govern the Bay Club shared-member billing system. They are intended to reduce accounting mistakes and keep the workflow reproducible across primary-membership groups without exposing private member data.

## Principles

- Evidence first: every monthly calculation must trace back to statement lines, files, commands, docs, and explicit assumptions.
- Do not make unsupported assumptions. Flag uncertainty instead.
- Be objective and detail-oriented. Separate evidence, rationale, conclusions, and preferences.
- Capture decisions as they happen, including product, workflow, validation, architecture, and implementation decisions.
- Keep important context explicit in docs. Avoid tribal knowledge.
- No hacks, duplicate paths, compatibility shims, or half-migrations unless explicitly approved and documented.
- Delete obsolete docs or mark them superseded with dated replacements.
- Treat automated checks as evidence, not conclusions.
- Turn bugs into durable learning: cause, coverage gap, fix, and retest requirement.
- Avoid turning summary wording into accidental product intent.
- Keep common docs role-based and public-safe. Real names, member IDs, payment details, statements, reports, rosters, rollups, and private decision records belong in a membership adapter.
- Default to local-first storage. Future frontend workflows must keep real billing data in the user's browser, local filesystem, private repo, or explicit export unless the user opts into another adapter.
- Treat storage as a port. Billing rules should not depend on whether data comes from files, a private repository, browser storage, or an import bundle.
- Do not add cloud sync, hosted persistence, telemetry, or collaboration for private billing data without an explicit opt-in design record.

## Monthly Report Standard

Each monthly report must include:

- Source statement provenance.
- Rule and charge-type version dates.
- Commands run.
- Statement-line classification.
- Assumptions.
- Exceptions.
- Validation results.
- Footnotes for unusual balance or payment patterns.
- Membership adapter root and membership group ID.
- Privacy-boundary checks when files are prepared for Git or sharing.

If evidence conflicts with a rule, stop and document the conflict before changing calculations.
