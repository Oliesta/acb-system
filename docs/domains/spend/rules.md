# Spend Ledger Rules

## Responsibility
Keeps a public, line-by-line record of how each awarded tender's funds are used. Issues ACB references. Never holds or moves money. See [ADR-007](../../architecture/decision-records/ADR-007-tender-spend-ledger.md).

## Invariants
- SPD-INV-1: Budget = award value + published variations.
- SPD-INV-2: Sum of line item budgets = budget.
- SPD-INV-3: Every ACB reference is unique across the whole system and never reused.

## Budget rules
- SPD-001: A ledger MUST be opened with line items taken from the contract's bill of quantities or pricing schedule. Each line has a name, a Rand budget and a description of what it covers.
- SPD-002: Line items MUST NOT overlap. Each kind of cost belongs to exactly one line.
  Valid: scoreboards only in "Seating and fixtures". Invalid: scoreboards in both "Seating and fixtures" and "Equipment and furniture".
- SPD-003: Amounts MUST be in Rand. Ledger entries are records only. They MUST NOT be tokens, have no value, and cannot be transferred.
- SPD-004: Moving budget between lines MUST be recorded as a reallocation with a reason. A reallocation over 10% of either line's original budget MUST be flagged. (Proposed threshold.)
- SPD-005: Every drawdown from a contingency line MUST state what it paid for.

## Funds in
- SPD-006: Each payment the contractor receives from the public body MUST be recorded as "funds in", with its date, amount and source: public body data, contractor record, or both. When both exist and differ, both are shown.

## Spend entries
- SPD-007: Each order, purchase, subcontract payment or payroll run MUST be recorded as a spend entry with: line item, amount (VAT shown separately), payee, description, date, and quantity and unit price where they apply.
- SPD-008: The payee MUST be a company identified by registered name and registration number, or "Payroll" for wages.
- SPD-009: Recording an entry issues an ACB reference. The reference MUST appear on the matching order or invoice.
  Valid: `ACB-2026-STD01-000123`. Invalid: an invoice paid from the project with no ACB reference.
- SPD-010: An entry has two stages: **Committed** (order placed, reference issued) and **Paid** (payment made, proof of payment hash attached). Invoice files are hashed when uploaded.
- SPD-011: An entry MUST be recorded within 5 working days of the order or payment. Later entries are marked late.
- SPD-012: A spend MUST NOT take a line below zero. The contractor must record a reallocation first.
- SPD-013: Entries are append-only and signed by the contractor's account. A correction is a reversing entry with a reason, linked to the original.

## Checking entries
- SPD-014: Anyone with an ACB reference MUST be able to look it up and see: amount, line item, payee company, date and stage.
- SPD-015: A payee MAY confirm an entry using a code sent with the reference. Confirmed entries are shown as confirmed. Payee disagreement MUST be shown and feeds the flags.
- SPD-016: The portal MUST show the **unaccounted balance**: funds in minus paid spend entries.

## Payroll
- SPD-017: Wages MUST be published as totals per line item per pay period, with the number of workers. Individual wage entries MUST be stored off-chain and encrypted (see [ADR-003](../../architecture/decision-records/ADR-003-personal-information-off-chain.md)).
- SPD-018: Each worker MUST receive a private ACB reference on their payslip, so they can check their own entry was recorded with the right amount. The lookup MUST NOT show the worker's name.

## Edge Cases
- **One invoice, several line items:** one entry per line, each with its own reference. The invoice carries all of them.
- **Reference reused on a second invoice:** the second use is flagged.
- **Order cancelled:** reversing entry, reference stays visible as cancelled.
- **Retention money held back:** recorded as funds not yet received, not as spend.
- **Contractor stops recording:** the unaccounted balance grows and triggers a flag.
- **Contractor does not take part:** the contract record shows "spend ledger: not participating".
- **Subcontractor spends:** recorded as one entry by the main contractor. Nested ledgers for subcontractors MAY be added in Phase 4.

## Acceptance Criteria
- Every Paid entry has a reference, a line item and a proof of payment hash.
- A worker's payslip reference shows their amount and pay period, and nothing that identifies them.
- The unaccounted balance is visible on every contract page with a ledger.

## Rule Ownership
| Rule ID | Module | Test |
|---------|--------|------|
| SPD-001 to SPD-018 | Spend ledger service, Contractor portal, Reference lookup | Planned |

## Owner
@Oliesta
