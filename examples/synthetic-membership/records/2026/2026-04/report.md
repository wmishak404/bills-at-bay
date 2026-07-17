# April 2026 Bay Club Shared-Member Billing Report

Report version date: 2026-07-16
Rule version date: 2026-07-16
Charge-type version date: 2026-07-16
Membership profile version date: 2026-07-16
Membership group ID: `synthetic-bayclub-example`

## Summary

- Source statement evidence: `records/2026/2026-04/statement-lines.csv`
- Billing date: 2026-04-01
- Billing period: 2026-04-01 through 2026-04-30
- Current primary member: Alex Primary
- Monthly roster: Alex Primary, Blair Shared, Casey Shared
- Active member count: `3`
- Allocated member-charge total: `$612.01`

## Statement Line Classification

| Date | Reference | Description | Amount | Charge type | Allocation |
| --- | --- | --- | ---: | --- | --- |
| 2026-03-16 | C EXAMPLE-001 | Payment - Thank You | `-$600.00` | Payment | Ignored accounting artifact. |
| 2026-03-16 | T EXAMPLE-002 | Credit Card Surcharge | `$12.01` | Credit card surcharge | Split evenly by active member count for the April statement month. |
| 2026-04-01 | T EXAMPLE-003 | April Dues | `$300.00` | Monthly dues | Included in dues total; primary member line. |
| 2026-04-01 | T EXAMPLE-004 | April Dues (EXAMPLE-SHARED-002 B Shared) | `$150.00` | Monthly dues | Included in dues total; Blair Shared. |
| 2026-04-01 | T EXAMPLE-005 | April Dues (EXAMPLE-SHARED-003 C Shared) | `$150.00` | Monthly dues | Included in dues total; Casey Shared. |

## Calculation

```text
300.00 + 150.00 + 150.00 = 600.00
600.00 / 3 active members = 200.00 per member
```

```text
Credit Card Surcharge                 12.01
12.01 / 3 active members = 4.003333...
Shared member share = 4.00
Primary member share = 4.01
Rounding residual assigned to primary member = 0.01
```

## Member Charges

| Member | Role | Dues share | Shared fee share | Member-change charges | Court fees | Guest fees | Pro shop sales | Unknown fees | Total due | Payment tracking |
| --- | --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | --- |
| Alex Primary | Primary member | `$200.00` | `$4.01` | `$0.00` | `$0.00` | `$0.00` | `$0.00` | `$0.00` | `$204.01` | No default payment row |
| Blair Shared | Shared member | `$200.00` | `$4.00` | `$0.00` | `$0.00` | `$0.00` | `$0.00` | `$0.00` | `$204.00` | Pending |
| Casey Shared | Shared member | `$200.00` | `$4.00` | `$0.00` | `$0.00` | `$0.00` | `$0.00` | `$0.00` | `$204.00` | Pending |

## Validation

- Every synthetic statement line maps to a documented charge type or ignored accounting artifact.
- Monthly roster and active member count come from April dues lines.
- Member charges sum to `$612.01`.
- Monthly CSVs match rollup CSVs.
