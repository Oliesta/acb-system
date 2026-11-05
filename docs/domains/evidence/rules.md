# Evidence Rules

## Responsibility
Receives and moderates community observations, and runs the community watchdog programme.

## Invariants
- EVD-INV-1: Every evidence item has a hash taken at capture or upload, and that hash never changes.

## Rules
- EVD-001: Original submissions MUST be stored encrypted. Only a moderated, redacted copy is published.
- EVD-002: Site photos MUST be captured inside the field app to count as verified observations. Gallery uploads MAY be accepted but MUST be labelled unverified.
- EVD-003: An image whose hash, or near-duplicate fingerprint, matches another submission MUST be flagged for moderation.
- EVD-004: GPS position MUST be checked against the project site. A position outside the site MUST be marked, not silently accepted or rejected.
- EVD-005: An observation MUST be linked to a contract record and, where possible, a listed deliverable.
- EVD-006: An observation is **verified** only when 2 or more independent watchdogs report the same thing, or 1 watchdog's in-app evidence is confirmed by a moderator. Only verified observations can feed flags.
- EVD-007: Watchdog identity MUST NOT be published or shared with suppliers or public bodies.
- EVD-008: Observations MUST describe what was seen, not accuse people. Moderators MUST remove accusations, names and personal information before publication.

## Edge Cases
- **Photo shows a person:** faces and number plates MUST be blurred on the public copy.
- **Duplicate upload:** stored once, linked twice.
- **Malicious reports:** a watchdog with 3 observations contradicted by others is suspended pending review.
- **Device clock wrong:** server receive time is also recorded. A gap over 24 hours is marked.
- **Site has restricted access:** watchdogs MUST NOT enter restricted sites. Observations are from public places only.

## Watchdog Programme
Watchdogs are trained community members who report what they can see on public project sites. Training covers what to look for, staying safe, staying on public ground, and their protections under the Protected Disclosures Act where relevant. A full programme guide is a follow-up for Phase 3.

## Acceptance Criteria
- No public observation contains a face, number plate, name or ID number.
- An unverified observation never triggers a flag.

## Rule Ownership
| Rule ID | Module | Test |
|---------|--------|------|
| EVD-001 to EVD-008 | Field app, Observation moderation | Planned |

## Owner
@Oliesta
