# Payments Rules

## Responsibility
Runs the payment release gate. Decides whether a milestone payment may be authorised, collects approvals and sends authorisations to the public body's financial system. Holds no funds, see [ADR-001](../../architecture/decision-records/ADR-001-funds-stay-on-government-rails.md), which owns PAY-001 and PAY-007.

## Invariants
- PAY-INV-1: At most one authorisation exists per milestone.
- PAY-INV-2: Authorised value never exceeds milestone value.

## Rules
- PAY-002: A release MUST be approved by at least 2 approvers in separate roles (for example project manager and CFO delegate). The exact N of M is set per public body.
- PAY-003: A person who verified the milestone MUST NOT approve its release.
- PAY-004: An invoice MUST be rejected if its file hash, or the pair (supplier CSD number, invoice number), already exists anywhere in the system.
- PAY-005: Supplier CSD status (registered, tax compliant, bank account verified) MUST be checked within 24 hours before each release, not only at award.
- PAY-006: If any check cannot run (CSD unavailable, budget data missing), the release MUST wait. It MUST NOT pass by default.
- PAY-008: An approval MUST expire after 10 working days if the release is not sent.

## Edge Cases
- **Bank account changed since award:** release waits until CSD shows the new account as verified, and the change is shown on the portal.
- **Approver leaves:** pending approvals by that person are void.
- **Same person in two roles:** counts as one approver.
- **Payment made outside the gate:** see PAY-007 in ADR-001.

## Acceptance Criteria
- A release cannot be sent with one approver, or with an approver who verified the milestone.
- A CSD outage causes waiting releases, never passed releases.

## Rule Ownership
| Rule ID | Module | Test |
|---------|--------|------|
| PAY-002 to PAY-008 | Payment release gate, Supplier checks | Planned |

## Owner
@Oliesta
