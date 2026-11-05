# Tenders Rules

## Responsibility
Builds one public record per tender and contract from source data: notice, award, value, supplier, variations and expected delivery.

## Invariants
- TND-INV-1: Every contract record has exactly one public body.
- TND-INV-2: Every value on a record has a source (see [Sources rules](../sources/rules.md)).

## Rules
- TND-001: A record MUST be keyed by the public body and the tender number as published. A contract with no published tender number MUST be shown as "not advertised", which is itself a flag input.
  Valid: `DPW-2026-0142` from the Department of Public Works. Invalid: a record with no public body.
- TND-002: Suppliers MUST be identified by registered company name and, where published, CSD supplier number or company registration number.
- TND-003: A record MUST show the timeline: advertised, closing, awarded, expected completion, and any published changes.
- TND-004: Published variations (changes to value or scope) MUST be added as new events, never by overwriting the original value.
- TND-005: Where a project has published deliverables or milestones, they MUST be listed so community observations can be matched to them.

## Edge Cases
- **Consortium or joint venture:** each member is listed.
- **Cancelled tender:** stays visible, marked cancelled with the source of the cancellation.
- **Re-advertised tender:** linked to the original.
- **Award published without a notice:** shown, and feeds the "not advertised" flag.

## Acceptance Criteria
- Any record shows its full timeline and sources on one page.

## Rule Ownership
| Rule ID | Module | Test |
|---------|--------|------|
| TND-001 to TND-005 | Contract record builder | Planned |

## Owner
@Oliesta
