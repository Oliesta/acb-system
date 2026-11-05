# Disclosure Rules

## Responsibility
Decides what the Glass Pipe portal and open data API show.

## Rules
- DSC-001: For every contract the portal MUST show: public body, supplier name and CSD number, tender reference, award value, variations, milestones, verification decisions with reasons, and payments.
- DSC-002: The portal MUST NOT show personal information of individuals. Supplier company names are not personal information. Sole proprietor names MAY be shown only where already published on the eTender Publication Portal.
- DSC-003: All public data MUST be downloadable in a machine-readable format, and SHOULD follow the Open Contracting Data Standard.
- DSC-004: Watchdog submissions MUST be shown no earlier than 72 hours after submission, with location coarsened to the site, not the exact point.
- DSC-005: Flags (late decisions, duplicate evidence, unmatched payments, split contracts) MUST be shown next to the contract they relate to.
- DSC-006: Each page MUST link to the on-chain anchor that covers its data.

## Edge Cases
- **POPIA deletion request:** personal information is deleted off-chain. Public events stay, with the reference removed.
- **Wrong data published:** corrected by a new event. The original stays visible, marked as corrected.

## Acceptance Criteria
- An automated scan of every public page and file finds no SA ID numbers, bank account numbers or phone numbers.

## Rule Ownership
| Rule ID | Module | Test |
|---------|--------|------|
| DSC-001 to DSC-006 | Glass Pipe portal | Planned |

## Owner
@Oliesta
