# YYYY-MM Bay Club Shared-Member Billing Report

Report version date: YYYY-MM-DD
Rule version date: YYYY-MM-DD
Charge-type version date: YYYY-MM-DD
Membership profile version date: YYYY-MM-DD
Membership group ID: `replace-with-group-id`
Membership adapter root: `memberships/<group-id>/`

## Summary

- Source statement: `records/YYYY/YYYY-MM/statement.pdf`
- Billing date: YYYY-MM-DD
- Billing period: YYYY-MM-DD through YYYY-MM-DD
- Statement balance due:
- Current primary member:
- Monthly roster:
- Active member count:
- Allocated member-charge total:

## Evidence And Provenance

- Statement file SHA-256:
- Statement membership number observed:
- Extraction method:

Commands run from the membership adapter root:

```bash
shasum -a 256 records/YYYY/YYYY-MM/statement.pdf
```

## Statement Line Classification

| Date | Reference | Description | Amount | Charge type | Allocation |
| --- | --- | --- | ---: | --- | --- |

## Monthly Roster

The monthly roster was inferred from dues lines.

| Member | Role | Statement evidence | Member identifier observed |
| --- | --- | --- | --- |

Active member count:

## Calculation

Document dues, recognized shared fees, member-change charges, direct charges, ignored accounting artifacts, and rounding residuals.

## Member Charges

| Member | Role | Dues share | Shared fee share | Member-change charges | Court fees | Guest fees | Pro shop sales | Unknown fees | Total due | Payment tracking |
| --- | --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | --- |

## Exceptions And Footnotes

- Unknown fees:
- Unmapped aliases:
- Member-change attribution exceptions:
- Unusual balance/payment patterns:

## Assumptions

- 

## Validation

- Every statement line maps to a documented charge type or ignored accounting artifact.
- Monthly roster and active member count come from dues lines.
- Monthly CSVs match adapter rollup CSVs.
- Private adapter files remain outside public Git tracking.
