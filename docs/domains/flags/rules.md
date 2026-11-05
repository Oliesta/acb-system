# Flags Rules

## Responsibility
Calculates and publishes risk indicators on contract records and spend ledgers. A flag says "this is worth a closer look". It is **never** a finding of wrongdoing.

## Invariants
- FLG-INV-1: Every flag is produced by a published, versioned flag definition.

## Rules
- FLG-001: Every flag definition MUST be published with its method, data inputs and thresholds before it is used.
- FLG-002: Flags MUST be worded as facts and indicators, not accusations.
  Valid: "Awarded 9 days after the supplier was registered." Invalid: "Fraudulent award."
- FLG-003: Flags MUST be calculated from sourced data only, and every flag MUST link to the facts that triggered it.
- FLG-004: A named supplier or public body MUST be able to submit a reply to any flag. Replies MUST be shown next to the flag within 5 working days, unless they contain personal information or abuse. (Proposed timing.)
- FLG-005: A flag MUST NOT be based on a single unverified community observation.
- FLG-006: Flags MUST NOT name individual people.
- FLG-007: A change to a flag definition MUST be a new version. Past flags keep the version that produced them.
- FLG-008: A flag that was wrongly calculated MUST be withdrawn with a visible correction note, not silently deleted.

## Initial flag definitions (proposed, to be tested in the Phase 2 pilot)
| ID | Flag | Trigger |
|----|------|---------|
| F01 | Not advertised | Award found with no matching tender notice and no published deviation reason |
| F02 | Single bid | Only one bid received, where bid counts are published |
| F03 | New company | Supplier registered fewer than 90 days before tender closing, or a payee registered fewer than 90 days before its first spend entry |
| F04 | Possible split | Same public body and supplier, 2 or more awards within 30 days, each just under a procurement threshold |
| F05 | Large variation | Published variations total more than 20% of the original value |
| F06 | Overdue | Expected completion date passed with no published completion |
| F07 | Not observed | Verified community observations show a deliverable missing after its due date |
| F08 | Price outlier | Unit price more than 2 times the median of comparable awards or spend entries |
| F09 | Data removed | A source removed or changed a record after collection |
| F10 | Unaccounted funds | Unaccounted balance ([SPD-016](../spend/rules.md)) above 10% of funds in for more than 30 days |
| F11 | Late entries | More than 10% of a month's spend entries recorded later than 5 working days |
| F12 | Large reallocation | A reallocation over 10% of a line's original budget ([SPD-004](../spend/rules.md)) |
| F13 | Disputed entry | A payee or worker disputes the amount, payee or existence of a spend entry ([SPD-015](../spend/rules.md)) |
| F14 | Spend ahead of progress | A line is more than 75% spent, or payroll worker counts are more than 2 times observed counts, while verified observations show the work has not reached that stage |
| F15 | Unconfirmed payee | A spend entry over R100,000 not confirmed by its payee within 30 days |
| F16 | Not participating | A contract with no spend ledger, where participation was a contract condition |

## Edge Cases
- **Missing data:** a flag that needs data that is not published MUST NOT fire. Missing publication may be its own flag (F01).
- **Reply disputes the facts:** the flag stays, the reply is shown, and the facts are rechecked within 10 working days.
- **Legal demand to remove:** handled under the takedown process in [security.md](../../architecture/security.md), never by silent removal.

## Acceptance Criteria
- Every flag on the portal links to its definition version and its triggering facts.
- No flag text names an individual.

## Rule Ownership
| Rule ID | Module | Test |
|---------|--------|------|
| FLG-001 to FLG-008 | Flag engine, Right of reply | Planned |

## Owner
@Oliesta
