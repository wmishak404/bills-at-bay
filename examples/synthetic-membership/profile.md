# Membership Profile

Version date: 2026-07-16
Last updated: 2026-07-16

## Purpose

This synthetic profile demonstrates the private adapter shape without using real member data.

## Account Context

- Membership group ID: `synthetic-bayclub-example`
- Club: Bay Club Example City
- Statement membership number observed: `EXAMPLE-PRIMARY-001`
- Current primary member: Alex Primary
- Primary-member status evidence: Synthetic April 2026 statement lines include the primary dues line.
- Payment destination: primary member
- Default tracked payment method for shared members: Venmo
- Payment details: not recorded in synthetic fixtures

## Known Members

| Canonical name | Role | Statement aliases observed | Member identifiers observed | Notes |
| --- | --- | --- | --- | --- |
| Alex Primary | Primary member | `Alex Primary`, primary dues line without parentheses | `EXAMPLE-PRIMARY-001` | Synthetic primary member. |
| Blair Shared | Shared member | `B Shared` | `EXAMPLE-SHARED-002` | Synthetic shared member. |
| Casey Shared | Shared member | `C Shared` | `EXAMPLE-SHARED-003` | Synthetic shared member. |

## Profile Rules

- This profile is not the monthly roster. The monthly roster must be inferred from each statement's dues lines.
- Preserve dated group-specific history in this adapter's `decisions/` folder.
