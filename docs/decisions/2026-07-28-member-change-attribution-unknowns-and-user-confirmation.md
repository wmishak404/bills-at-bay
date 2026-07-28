# Member-Change Attribution Unknowns And User Confirmation

Version date: 2026-07-28
Status: Implemented

## Decision

Some member-change attribution questions cannot be solved from Bay Club billing data alone. A statement can show prorated `Membership Dues` adjustments, processing fees, roster changes, and transaction dates, but it may not identify which changed shared member maps to which prorated charge.

When billing evidence cannot identify the affected member or member-to-date mapping, the system must mark the attribution as unknown and ask the user for confirmation before converting the amount into a payment request.

## Required Behavior

- Do not silently assign unresolved member-change charges to the primary member.
- Do not guess which affected changed shared member maps to a dated prorated charge.
- Record the unresolved charge as an attribution exception.
- Preserve the statement evidence and the possible affected changed shared members.
- Ask the user calculating the bill to confirm next actions.

## Options To Present

When asking the user, present options neutrally:

- provide the actual member-change dates or member names, then assign charges accordingly;
- leave the amount pending until better evidence is available;
- choose a consent-based allocation override, such as splitting an otherwise-unattributable prorated-dues total evenly across the affected changed shared members.

Only apply an override when the user calculating the bill chooses it. The user's consent is part of the accounting evidence.

## Documentation Requirement

If a user chooses an override, document:

- why billing data was insufficient;
- which alternatives were presented;
- which option the user chose;
- the affected members;
- the allocation math;
- the effect on payment requests.

This keeps the reusable billing system conservative while still allowing the person responsible for the bill to make a transparent, consent-based allocation decision.
