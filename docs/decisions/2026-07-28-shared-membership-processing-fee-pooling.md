# Shared Membership Processing Fee Pooling

Version date: 2026-07-28
Status: Implemented

## Decision

`Shared Membership Processing Fee` amounts can vary because of Bay Club promotions or discounts. When multiple affected changed shared members have processing fees in the same statement-month billing packet, sum the processing-fee lines and divide the total evenly across those affected changed shared members.

Example:

```text
Shared Membership Processing Fee      100.00
Shared Membership Processing Fee       50.00
Processing-fee pool total             150.00
150.00 / 2 affected changed members =  75.00 each
```

Keep each printed statement line as evidence. Do not infer that a higher processing-fee amount belongs entirely to one affected member when the affected changed-member set is known.

## Scope

This pooling rule applies only to `Shared Membership Processing Fee` lines. It does not change prorated `Membership Dues` adjustments, which remain attributed by statement evidence, roster deltas, transaction dates, prorated dues math, and user-provided member-change context.

## Impact

- `docs/rules.md` moved to version date `2026-07-28`.
- `docs/charge-types.md` moved to version date `2026-07-28`.
- Existing monthly packets with multiple processing-fee amounts for multiple affected changed shared members should be recalculated under this rule when payment requests have not already been finalized.
