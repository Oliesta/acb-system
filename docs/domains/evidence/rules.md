# Evidence Rules

## Responsibility
Receives, stores and redacts evidence. Runs the community watchdog programme.

## Invariants
- EVD-INV-1: Every evidence item has a hash taken at capture or upload, and that hash never changes.

## Rules
- EVD-001: Original evidence MUST be stored encrypted. A redacted copy MUST be produced for the portal.
- EVD-002: Site photos from inspectors MUST be captured inside the field app. Uploads from the gallery MUST NOT count as inspection evidence.
- EVD-003: An image whose hash, or near-duplicate fingerprint, matches evidence on another milestone MUST be flagged.
- EVD-004: GPS position MUST be checked against the registered site boundary. A position outside the boundary MUST be flagged, not silently accepted or rejected.
- EVD-005: Evidence captured offline MUST keep its capture time and hash, and MUST sync within 7 days. Later syncs are flagged.
- EVD-006: Watchdog submissions MUST NOT accept or reject a milestone on their own. A watchdog report that conflicts with an Accepted decision MUST trigger re-inspection by a different inspector.
- EVD-007: Watchdog identity MUST NOT be shown publicly or to the supplier or public body.
- EVD-008: Invoices MUST have bank details, ID numbers and personal contact details redacted before publication.

## Edge Cases
- **Photo of a person:** faces MUST be blurred on the public copy.
- **Duplicate upload by same person:** stored once, linked twice.
- **Malicious watchdog reports:** a watchdog with 3 reports contradicted by independent re-inspection is suspended pending review.
- **Device clock wrong:** server receive time is also recorded. A gap over 24 hours is flagged.

## Watchdog Programme
Watchdogs are trained community members who report what they see on public project sites. They are covered by these rules and SHOULD be informed of their protections under the Protected Disclosures Act. A detailed programme guide is a follow-up.

## Acceptance Criteria
- No public file contains an unredacted ID number, bank account number or face.
- A gallery photo cannot be attached to an inspection.

## Rule Ownership
| Rule ID | Module | Test |
|---------|--------|------|
| EVD-001 to EVD-008 | Evidence service, Field app | Planned |

## Owner
@Oliesta
