# Sources Rules

## Responsibility
Collects procurement data from public sources, keeps snapshots, and records where every fact came from.

## Invariants
- SRC-INV-1: Every fact on the portal traces back to at least one source record.

## Rules
- SRC-001: Data MUST come only from lawful public sources, community observations, or data a party chose to share. See [ADR-005](../../architecture/decision-records/ADR-005-independent-transparency-platform.md).
- SRC-002: Every source record MUST store: source name, source URL or reference, retrieval time, and a hash of the retrieved content.
- SRC-003: A snapshot of every retrieved document MUST be archived, so later removal or change at the source can be proven.
- SRC-004: If a source changes or removes a record already collected, that change MUST be recorded as a new event and shown on the portal.
- SRC-005: Collectors MUST respect each source's terms of use and robots rules, and MUST NOT send more than 1 request per second to any single source. (Proposed limit.)
- SRC-006: Voluntarily shared data MUST be labelled as such, and MUST NOT overwrite data from an independent public source.

## Initial sources (to be confirmed)
| Source | What it provides |
|--------|------------------|
| eTender Publication Portal | Tender notices and awards |
| Public body websites | Award notices, bid committee results, deviation reports |
| National Treasury budget and municipal finance publications | Budgets and spending reports |
| Auditor-General reports | Irregular expenditure findings |
| CIPC company records (where public) | Company registration date and status |
| Community observations | Site reports, see [Evidence rules](../evidence/rules.md) |

## Edge Cases
- **Two sources disagree** (for example on award value): both values are shown with their sources. The system MUST NOT silently pick one.
- **Source offline:** collection retries later. Existing data stays, marked with its last retrieval time.
- **Scanned PDF only:** text extracted by OCR MUST be marked as machine-read until checked by a person.
- **Same record from two sources:** linked as one record with two sources.

## Acceptance Criteria
- For any fact on the portal, a user can open its source reference and the archived snapshot.

## Rule Ownership
| Rule ID | Module | Test |
|---------|--------|------|
| SRC-001 to SRC-006 | Source collectors, Snapshot archive | Planned |

## Owner
@Oliesta
