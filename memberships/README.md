# Private Membership Adapters

This directory is the local/private data boundary.

Each real primary-membership group should live in `memberships/<group-id>/` with:

```text
profile.md
records/
rollups/
decisions/
```

Real membership folders are ignored by Git by default because they can contain names, member IDs, payment details, statements, reports, rosters, rollups, and other generated private outputs.

Use `examples/synthetic-membership/` and `templates/` for public-safe fixtures and reusable starter files.
