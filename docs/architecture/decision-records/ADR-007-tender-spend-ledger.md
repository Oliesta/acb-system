# ADR-007: Tender spend ledger with ACB references
Status: Proposed
Date: 2026-11-05
Owner: @Oliesta

## Context
This is the original ACB idea. When a tender is awarded (for example R10,000,000 for a village stadium), the public should see how that money is used, item by item, while the project runs. Today the public sees, at best, the award value. The SIU only sees the spending after the money is gone.

The original draft described a "blockchain wallet" holding 10,000,000 credits that are debited as money is spent. The system must not manage funds ([IND-001](ADR-005-independent-transparency-platform.md)), so the wallet has to be a **mirror record**, not a store of value.

## Decision
Each tender on the platform has a **spend ledger**: a budget equal to the award value, split into line items taken from the contract's bill of quantities or pricing schedule. The contractor records every order, purchase and payroll run against a line item. Each entry gets a unique **ACB reference**, which MUST be printed on the matching invoice or order. Entries are signed by the contractor, append-only, public, and anchored on-chain ([ADR-002](ADR-002-public-chain-anchoring.md)). Anyone holding an invoice can look up its ACB reference and check that the recorded amount and line item match.

## Alternatives
- Real crypto wallet holding the funds: rejected, see [ADR-001](ADR-001-funds-stay-on-government-rails.md). Public funds cannot legally be held this way.
- Tokens or "credits" with their own units: rejected because they add nothing over Rand amounts, invite confusion with cryptocurrency, and could fall under crypto asset regulation. The ledger uses Rand, and its entries have no value and cannot be transferred.
- Read-only bank feed from the contractor's project account: not rejected. It is the strongest evidence, but needs bank and contractor agreement. Kept as an optional Phase 4 addition.
- Only track what the public body pays the contractor: rejected because most corruption hides in how the contractor spends the money (inflated invoices, fake suppliers, ghost workers).

## Consequences
- Easier: every Rand of a tender has a public, line-by-line story. Suppliers and workers who hold an invoice or payslip become checkers, because they can see if their entry was inflated or invented.
- Harder: the ledger only shows what the contractor records. Missing entries must be visible as an **unaccounted balance**, and recorded entries must be checked against payee confirmations and site observations.

## Rules
The ledger rules are in [Spend ledger rules](../../domains/spend/rules.md) (`SPD`).

## Review Trigger
A bank offers read-only project account feeds, or the pilot shows contractors cannot record entries within 5 working days.

## References
- Documentation: [Spend ledger rules](../../domains/spend/rules.md), [Stadium example](../../context/example-stadium.md), [Architecture](../architecture.md)
- Tests or validation: none yet
