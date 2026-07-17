# Billing Rules

Version date: 2026-07-16
Last updated: 2026-07-16

## Purpose

These rules define how to split a Bay Club shared-member statement. They are role-based so the system can be reused by other shared-member groups.

See `charge-types.md` for the charge taxonomy. Use the selected private membership adapter's `profile.md` for that group's member names, aliases, member numbers, and payment context.

## Core Terms

- Primary member: the account holder/payer who pays the full Bay Club bill.
- Shared members: members who reimburse the primary member.
- Monthly roster: the primary member plus shared members appearing in that month's dues lines.
- Active member count: the number of people in the monthly roster. This is the divisor for shared dues and recognized shared fees.

## Statement Month And Service Period

Bay Club statements are sent at the beginning of the month. Treat a statement dated on the first day of a month as the billing packet for that full calendar month.

Example: a statement dated `2026-07-01` is the July billing packet and covers July 1 through July 31.

Some line items can carry transaction dates from the prior month even though they appear on the current statement. Classify those lines by charge type and apply the current statement-month allocation policy unless a documented exception says otherwise.

## Roster Rule

Infer the monthly roster and active member count from that month's dues lines.

- If a shared member appears in a dues line, include them in the monthly roster and active member count.
- If a previously known shared member does not appear in the month's dues lines, exclude them from that month's roster and count.
- If a new shared member appears in the month's dues lines, include them and add their observed alias or member number to the selected membership adapter's `profile.md`.
- The primary member is included when the statement has a primary-member dues line.

Do not use a fixed roster as the divisor. Member names and active member count are month-specific variables.

## Dues Rule

For monthly dues:

1. Identify all dues lines for the billing month, such as `April Dues`.
2. Sum all dues line amounts, including the primary member's dues line and shared-member dues lines.
3. Divide the dues total evenly by the active member count.
4. Assign the same dues share to every person in the monthly roster.

Statement dues amounts are inputs to the aggregate only. Individual invoice dues prices do not determine the final reimbursable dues share.

## Recognized Shared Fees

Split recognized shared fees evenly by the active member count. Current recognized shared fees are:

- `Credit Card Surcharge`

Credit card surcharge caveat: Bay Club appears to assess the surcharge against the prior balance/payment cycle. Because it is expected to recur around the same amount each month, this system allocates the surcharge with the current statement month by default. Record this caveat in monthly reports when a surcharge is present.

See `charge-types.md` before adding a new recognized shared fee.

## Member-Change Charges

Member-change charges are not split evenly across the monthly roster by default.

Current member-change charge types are:

- `Membership Dues` lines that are not the month-specific dues lines, such as `June Dues`.
- `Shared Membership Processing Fee`.

`Shared Membership Processing Fee` is a member-change processing charge. Use the statement amount as printed. Do not break a processing-fee line into multiple smaller fees unless Bay Club, Connect, or other member-change evidence supports that breakdown. Treat each processing-fee line as its own dated member-change charge group.

Plain `Membership Dues` lines can represent prorated dues tied to member additions or subtractions. Treat them as member-change charges, not recurring shared fees.

Assign member-change charges to the affected added or deleted shared member.

If the statement line names the affected member, use that evidence. If it does not, infer the affected member from month-over-month roster changes, transaction dates, and prorated dues math. A member-change charge can appear on the next statement after the actual change date; still bill the shared member whose status changed.

If the affected member cannot be identified from statement evidence, roster deltas, or user-provided context, do not silently assign the charge to the primary member. Record an attribution exception and request the missing member-change context.

## Extras And Direct Charges

- Named court fees are assigned to the named member in the charge description.
- Unnamed court fees are assigned to the primary member.
- Pro shop charges are assigned to the primary member unless another member is explicitly named.
- Guest fees are assigned to the primary member by default and are not split evenly. If a future statement names a shared member for a guest fee, flag the line for review before assigning it away from the primary member.
- Unknown or undefined fees are assigned to the primary member by default and flagged as exceptions needing review. This default does not apply to known member-change charges.

## Ignored Accounting Artifacts

Ignore these statement lines in member charge calculations:

- `Previous Balance`
- `Payment - Thank You`

Still report these lines in the monthly report. A normal month is expected to have one previous balance line and one payment line. Flag unusual patterns, including missing payment lines, multiple payment lines, multiple previous balance lines, or balance/payment mismatches.

## Rounding

Calculate in dollars and cents. When an evenly split charge creates a residual penny or pennies, assign the residual to the primary member.

This keeps shared-member payment requests uniform and records the residual explicitly.

## Payment Tracking

By default, track only shared-member payments to the primary member.

- Do not create a default payment row for the primary member.
- Shared-member payment rows should default to pending until payment evidence is recorded.
- Venmo is the default tracked method unless the membership adapter profile or monthly evidence says otherwise.

## Versioning

Every monthly report must record:

- Rule version date.
- Charge-type version date.
- Membership profile version date used.
- Source statement file.
- Commands used to extract or validate evidence.
- Membership group ID and membership adapter root.

When rules change, update this file's version date and add a dated decision record. Use common docs for public-safe rule decisions and the selected membership adapter's `decisions/` folder for group-specific evidence or names.
