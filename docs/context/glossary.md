# Glossary

| Term | Meaning |
|------|---------|
| **ACB reference** | The unique reference issued when a spend entry is recorded, for example `ACB-2026-STD01-000123`. It is printed on the invoice or payslip so the holder can check the entry. |
| **Anchor** | Writing a single hash that summarises a batch of records to a public blockchain, so anyone can later prove the batch was not changed. See [ADR-002](../architecture/decision-records/ADR-002-public-chain-anchoring.md). |
| **Bill of quantities** | The priced list of work and materials in a construction contract. The source of a spend ledger's line items. |
| **Contract record** | The platform's single page per tender or contract, linking notice, award, variations, deliverables, observations and flags. |
| **CSD** | National Treasury Central Supplier Database. |
| **Deliverable** | A published, checkable item of work in a contract, for example "clinic roof completed". |
| **Flag** | A risk indicator calculated by a published method. A reason to look closer, never a finding of wrongdoing. See [Flags rules](../domains/flags/rules.md). |
| **Flag definition** | The versioned, published method that produces a flag. |
| **Funds in** | Payments the contractor received from the public body for a contract. |
| **Glass Pipe** | The public portal and open data API. |
| **Ledger** | The append-only record of all events in the system. Stored off-chain, anchored on-chain. |
| **Line item** | One budget line in a spend ledger, for example "Construction materials: R2,500,000". |
| **Moderator** | A trained reviewer who checks community observations before publication. |
| **Observation** | A community report of what is visible at a project site. **Verified** when it meets [EVD-006](../domains/evidence/rules.md). |
| **PAIA** | Promotion of Access to Information Act, 2000. Lets anyone request records from public bodies. |
| **Payee** | The company (or payroll) that a spend entry pays. |
| **Payee confirmation** | A payee confirming, with a private code, that a spend entry matches what they were paid. |
| **Personal information** | As defined in POPIA. Includes names, ID numbers, contact details, bank details and images of identifiable people. |
| **Public body** | A national or provincial department, municipality, public entity or state-owned company. |
| **Reply** | A response from a named supplier or public body to a flag, shown next to it. |
| **Snapshot** | An archived copy of a source document at the time it was collected. |
| **Source** | Where a fact came from: a public website, document or community observation. |
| **Spend entry** | A record of one order, purchase, subcontract payment or payroll run, against one line item. |
| **Spend ledger** | The per-tender record of budget lines, funds in and spend entries. A mirror of spending in Rand, not a wallet. See [ADR-007](../architecture/decision-records/ADR-007-tender-spend-ledger.md). |
| **Supplier** | The company awarded a contract. |
| **Unaccounted balance** | Funds in minus paid spend entries. Money the contractor received but has not shown how it was used. |
| **Variation** | A change to a contract's value or scope after award. |
| **Watchdog** | A trained community member who submits site observations. |
