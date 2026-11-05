# Milestones Rules

## Responsibility
Defines milestones, receives claims, assigns inspectors and records verification decisions.

## Invariants
- MIL-INV-1: A milestone is in exactly one state: Open, Claimed, Under verification, Accepted, Rejected, Paid, Closed.
- MIL-INV-2: A milestone can be Paid only after Accepted.

## Rules
- MIL-001: Each milestone MUST have a value and written acceptance criteria that an inspector can check on site.
  Valid: "Roof sheeting installed on blocks A to C, no visible gaps". Invalid: "Phase 2 progress".
- MIL-002: A claim MUST include an invoice and reference exactly one milestone.
- MIL-003: A claim on a Rejected milestone MUST be a new claim, linked to the previous one.
- MIL-004: Inspectors MUST be assigned at random from the eligible pool. The public body official and the supplier MUST NOT choose the inspector.
- MIL-005: A milestone above R1,000,000 MUST be verified by two inspectors who did not inspect each other's last 3 milestones. (Proposed threshold, to be confirmed.)
- MIL-006: An inspector with a declared or detected conflict of interest with the supplier MUST NOT be assigned.
- MIL-007: A verification decision MUST be one of Accepted, Rejected or Needs more evidence, and MUST give a reason.
- MIL-008: A verification decision SHOULD be made within 10 working days of the claim. Claims past 15 working days MUST be flagged on the portal.
- MIL-009: A supplier MAY dispute a Rejected decision once. The dispute MUST be decided by a different inspector.

## Edge Cases
- **No eligible inspector:** the claim waits and is flagged. It MUST NOT fall back to a hand-picked inspector.
- **Inspector disagreement:** if two inspectors disagree, a third is assigned at random.
- **Partial delivery:** a milestone is either met or not. Partial delivery needs a variation that splits the milestone.
- **Concurrent claims:** two claims on the same milestone at once: the second MUST be rejected.

## Acceptance Criteria
- Inspector assignment cannot be overridden by any role, including admin.
- Every decision shows its reason on the portal.

## Rule Ownership
| Rule ID | Module | Test |
|---------|--------|------|
| MIL-001 to MIL-009 | Verification service | Planned |

## Owner
@Oliesta
