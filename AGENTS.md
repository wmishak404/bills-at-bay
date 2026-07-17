# Bay Club Shared-Member Billing System

Version date: 2026-07-15
Last updated: 2026-07-16

## Purpose

This repository is a document-first accounting system for Bay Club shared-member bills. It separates reusable billing rules from private primary-membership adapters that hold real statements, profiles, reports, rosters, and rollups.

This is not a full app yet. Prefer clear files, traceable evidence, reproducible calculations, conservative assumptions, and local-first privacy boundaries.

## Required Reading Order

Before doing monthly billing work, read:

1. `docs/operating-principles.md`
2. `docs/rules.md`
3. `docs/charge-types.md`
4. `docs/local-first-architecture.md`
5. The selected private membership adapter profile, such as `memberships/<group-id>/profile.md`
6. The target month folder under `memberships/<group-id>/records/`

## Vocabulary

- Primary member: the account holder/payer who pays the full Bay Club bill.
- Shared members: members who reimburse the primary member.
- Monthly roster: the primary member plus shared members found in that month's dues lines.
- Active member count: the count of people in the monthly roster. Use this as the divisor for shared dues and recognized shared fees.

Use role-based wording in durable common docs. Names belong only in private membership profiles, statement evidence, monthly reports, and private decision records.

## Privacy Boundary

- Public/shareable files: common docs, rules, charge types, templates, architecture notes, and synthetic examples.
- Private/local files: real statements, membership profiles, member IDs, payment details, monthly reports, rosters, CSV rollups, exports, and anything generated from real statements.
- Private membership adapters live under `memberships/<group-id>/` and are ignored by Git by default.
- Future app storage must be local-first. Real billing data should stay in the user's browser, local filesystem, private repo, or explicit export unless the user opts into another storage adapter.

## Monthly Workflow

For each statement month:

1. Choose the membership adapter root, such as `memberships/<group-id>/`.
2. Store the source statement in `<adapter>/records/YYYY/YYYY-MM/statement.pdf`.
3. Extract and record statement evidence in `<adapter>/records/YYYY/YYYY-MM/report.md`.
3. Treat the statement dated `YYYY-MM-01` as the billing packet for that calendar month, covering `YYYY-MM-01` through the final day of that month.
4. Infer the monthly roster and active member count from the dues lines.
5. Classify each statement line using `docs/charge-types.md`.
6. Calculate member charges using `docs/rules.md`.
7. Record shared-member payment tracking in the monthly `payments.csv`.
8. Sync the monthly CSV rows into `<adapter>/rollups/member-charges.csv` and `<adapter>/rollups/venmo-payments.csv`.
9. Validate totals and document commands, assumptions, exceptions, and evidence.

## File Layout

```text
docs/
  operating-principles.md
  rules.md
  charge-types.md
  local-first-architecture.md
templates/
  membership-profile.md
  monthly-report.md
  charges.csv
  payments.csv
examples/
  synthetic-membership/
memberships/
  <group-id>/              # private, ignored by Git
    profile.md
    records/
      YYYY/
        YYYY-MM/
          statement.pdf
          report.md
          charges.csv
          payments.csv
    rollups/
      member-charges.csv
      venmo-payments.csv
    decisions/
```

Monthly folders are the audit source of truth inside each membership adapter. Rollups are synchronized per-adapter views for fast cross-month summaries.

## Validation Expectations

Every monthly report must show:

- Rule version date and charge-type version date.
- Statement provenance and commands used.
- Every statement line mapped to a charge type or exception.
- Monthly roster and active member count evidence.
- Charge math and rounding treatment.
- Ignored accounting artifacts and any unusual patterns.
- Unknown fees and review-needed exceptions.
- Reconciliation between monthly CSVs and rollup CSVs.
- Membership group ID in private CSV rows.
- Evidence that private adapter files are not staged for public Git history.

Treat automated checks as evidence, not final conclusions. If a bug is found, document the cause, coverage gap, fix, and retest requirement.
