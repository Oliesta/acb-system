# Tenders Rules

## Responsibility
Records tenders, awards, contracts and variations. Does not run the tender process itself.

## Invariants
- TND-INV-1: Every contract has exactly one public body and one supplier.
- TND-INV-2: The sum of milestone values equals the current contract value.

## Rules
- TND-001: A contract MUST reference its tender number as published on the eTender Publication Portal, or record the documented reason it was not advertised (for example an approved deviation).
  Valid: `tender_ref: "DPW-2026-0142"`. Invalid: empty tender reference with no deviation reason.
- TND-002: A supplier MUST be identified by CSD supplier number, not by name.
- TND-003: Award value, supplier and award date MUST be public from the moment the contract is registered.
- TND-004: A contract MUST have at least one milestone before any claim can be made.
- TND-005: A variation MUST record its reason and approver. A variation that takes total variations above 20% of the original contract value MUST need approval from a role above the original approver. (Proposed threshold, to be confirmed.)
- TND-006: Deviations from normal procurement (emergency, single source) MUST be flagged on the portal.

## Edge Cases
- **Duplicate registration:** the same tender number and supplier registered twice MUST be rejected.
- **Cancelled contract:** remaining unpaid milestones are closed. Paid milestones stay visible.
- **Split contracts:** several contracts with the same supplier and public body within 30 days that each fall just under a procurement threshold MUST be flagged for review.
- **Consortium or joint venture:** each member is recorded by CSD number.

## Acceptance Criteria
- A registered contract appears on the portal with award data within 1 hour.
- A variation over the threshold cannot be saved without the higher approval.

## Rule Ownership
| Rule ID | Module | Test |
|---------|--------|------|
| TND-001 to TND-006 | Contract registry | Planned |

## Owner
@Oliesta
