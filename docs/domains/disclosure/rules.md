# Disclosure Rules

## Responsibility
Decides what the Glass Pipe portal and open data API show.

## Rules
- DSC-001: For every contract the portal MUST show: public body, supplier, tender reference, timeline, values, variations, deliverables, verified observations, flags with replies, and sources.
- DSC-002: The portal MUST NOT show personal information of individuals. Company names are not personal information. Sole proprietor names MAY be shown only where already published by an official source.
- DSC-003: All public data MUST be downloadable in a machine-readable format, and SHOULD follow the Open Contracting Data Standard.
- DSC-004: Community observations MUST be published no earlier than 72 hours after submission, with location shown as the project site, not the exact point.
- DSC-005: Every flag MUST appear with its explanation, its definition version and any reply (see [Flags rules](../flags/rules.md)).
- DSC-006: Each page MUST link to the on-chain anchor that covers its data.
- DSC-007: Every page MUST state that flags are indicators for review, not findings of wrongdoing.

## Edge Cases
- **POPIA deletion request:** personal information is deleted off-chain. Public events stay, with the reference removed.
- **Wrong data published:** corrected by a new event. The original stays visible, marked as corrected.

## Acceptance Criteria
- An automated scan of every public page and file finds no SA ID numbers, bank account numbers or phone numbers.

## Rule Ownership
| Rule ID | Module | Test |
|---------|--------|------|
| DSC-001 to DSC-007 | Glass Pipe portal | Planned |

## Owner
@Oliesta
