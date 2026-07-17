# Charge Types

Version date: 2026-07-16
Last updated: 2026-07-16

## Purpose

This document defines known Bay Club statement charge types, matching patterns, allocation rules, default assignees, and exception behavior.

Use this file to classify every statement line before calculating member totals.

## Charge-Type Table

| Charge type | Match examples | Allocation rule | Default assignee | Report behavior |
| --- | --- | --- | --- | --- |
| Monthly dues | `April Dues`, `March Dues`, `May Dues (P12345678 A Member)` | Sum all month-specific dues lines, then split evenly by active member count. | Monthly roster | Include in dues calculation and roster evidence. |
| Member-change dues adjustment | `Membership Dues` when not part of a month-specific dues line such as `June Dues` | Assign to the affected added or deleted shared member using line evidence, roster deltas, transaction dates, and prorated dues math. | Affected changed shared member | Include under member-change charges; flag attribution if the changed member cannot be identified. |
| Credit card surcharge | `Credit Card Surcharge` | Split evenly by active member count for the current statement month, even when transaction timing suggests it relates to the prior balance/payment cycle. | Monthly roster | Include under recognized shared fees and document the timing caveat in the monthly report. |
| Shared membership processing fee | `Shared Membership Processing Fee` | Treat as a member-change processing charge; observed amounts are `$50.00` and `$100.00` for now. Use the statement amount as printed and assign it to the affected added or deleted shared member using line evidence, roster deltas, and related proration evidence. | Affected changed shared member | Include under member-change charges; flag attribution if the changed member cannot be identified. |
| Court fees | `Court Fees`, `Court Fee`, descriptions containing a member name or alias | Assign to named member when name or alias is present. | Primary member when unnamed | Include under court fees; document extraction evidence for the name match. |
| Pro shop sales | `Pro Shop Sales`, `Pro Shop` | Assign to named member when a member is explicitly named. | Primary member | Include under pro shop sales. |
| Guest fees | `Guest Fee`, `Guest Fees` | Assign to the primary member by default; do not split evenly. | Primary member | Include under guest fees. If a future statement names a shared member, flag for review before assigning away from the primary member. |
| Previous balance | `Previous Balance` | Ignore in member charge calculations. | None | Report as an ignored accounting artifact. |
| Payment | `Payment - Thank You` | Ignore in member charge calculations. | None | Report as an ignored accounting artifact. |
| Unknown or undefined fee | Any positive or negative line not matching a known type | Assign to primary member by default. | Primary member | Flag as exception needing review. |

## Monthly Dues Matching

A dues line is month-specific when the description contains a month name followed by `Dues`, with or without a member identifier in parentheses.

Examples:

- `April Dues`
- `April Dues (P12345678 A Member)`
- `April Dues (12345679 S Shared)`

The first dues line without parentheses is usually the primary member line, but confirm this against the membership profile and statement context. Do not rely on position alone if the statement format changes.

## Member-Change Charge Matching

`Membership Dues` without a month name is a member-change dues adjustment, not the recurring monthly dues split. It can represent prorated dues for an addition or subtraction.

`Shared Membership Processing Fee` is a member-change processing fee. Use the statement amount as printed.

Do not infer that a larger processing-fee amount equals multiple smaller fees unless Bay Club, Connect, or other member-change evidence supports that breakdown. A processing-fee line may represent a distinct processing charge, a bundled operation, or multiple underlying actions. Treat the line as one dated member-change charge group until there is better evidence.

When the statement does not name the affected member, use month-over-month roster deltas and proration evidence to infer the changed shared member. If the member still cannot be identified, record an attribution exception instead of assigning the charge to the primary member by default.

## Guest Fee Matching

`Guest Fee` lines are primary-member charges by default and are not split evenly.

When a statement does not include guest counts or names, do not infer guest count or rate from the amount alone.

## Statement Timing Caveat

Bay Club statements are sent at the beginning of the month and are treated as covering that calendar month. For example, a statement dated `2026-07-01` covers July 1 through July 31.

Some charges can show transaction dates before the statement month. The credit card surcharge is the known example: it may relate to the prior balance/payment cycle, but it is allocated with the current statement month by policy.

## Name And Alias Matching

Use the selected membership adapter's `profile.md` to map short statement labels to canonical member names.

Examples:

- `A Member` maps to a canonical member name in the private adapter profile.
- `S Shared` maps to a canonical shared-member name in the private adapter profile.

If a statement contains an unmapped alias, classify the line but flag the alias as an exception until the profile is updated.

## Change Control

When adding or changing a charge type:

1. Update this file's version date.
2. Add the new match pattern and allocation rule.
3. Document whether old monthly reports should be recalculated or left under their original charge-type version.
4. Add the decision to a dated plan or decision record.
