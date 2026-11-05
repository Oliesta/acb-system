# ACB System

**Anti-Corruption Blockchain System: an open-source platform that makes the use of public tender funds visible to the public, line by line, while projects are under way.**

| | |
|---|---|
| **Status** | Concept stage. Documentation first, no code yet |
| **Focus** | South African public procurement |
| **Maintainer** | [@Oliesta](https://github.com/Oliesta) |
| **Licence** | [MIT](LICENSE) |

## Contents

- [Background](#background)
- [Approach](#approach)
- [Worked example](#worked-example)
- [Capabilities](#capabilities)
- [Design principles](#design-principles)
- [Limitations](#limitations)
- [Roadmap](#roadmap)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [Security](#security)
- [Licence](#licence)
- [Contact](#contact)

## Background

When a public tender is awarded, the public can usually see the award value and the successful bidder. How the contractor then spends the money is not visible. Inflated invoices, payments to fictitious suppliers and non-existent workers typically come to light only through audits and Special Investigating Unit (SIU) investigations, after the funds have already been lost.

The ACB System aims to close that gap by making spending visible while there is still time to act.

## Approach

Each awarded tender has a **spend ledger**. The budget is divided into line items taken from the contract, and every order, purchase and payroll run is recorded against a line item.

Each entry receives a unique **ACB reference**, which is printed on the corresponding invoice or payslip. Anyone holding that document can look up the reference and confirm that the recorded amount, line item and payee are correct. Discrepancies are flagged publicly, together with signals from community site observations and published procurement data.

The ACB System **does not hold, manage, approve or move funds**. Payments continue through normal banking and government systems. The ledger is an independent, tamper-evident record of how the money was used. See [ADR-005](docs/architecture/decision-records/ADR-005-independent-transparency-platform.md) and [ADR-007](docs/architecture/decision-records/ADR-007-tender-spend-ledger.md).

## Worked example

A municipality awards a R10,000,000 tender to build a stadium in a village. The contractor's spend ledger opens with these line items:

| Line item | Budget |
|-----------|-------:|
| Site preparation | R500,000 |
| Design and planning | R750,000 |
| Construction materials | R2,500,000 |
| Labour and subcontractors | R3,500,000 |
| Seating and fixtures | R1,250,000 |
| Safety and security | R250,000 |
| Concessions and restrooms | R500,000 |
| Landscaping and site amenities | R250,000 |
| Equipment and furniture | R100,000 |
| Contingency | R500,000 |
| **Total** | **R10,000,000** |

The contractor orders 2,000 bags of cement for R190,000 and records the order against "Construction materials". The ledger issues reference `ACB-2026-STD01-000123`, which the supplier prints on its invoice. If the supplier's actual invoice was for R90,000, the supplier can dispute the entry, and the discrepancy is shown publicly on the contract record.

The full walkthrough is in the [village stadium example](docs/context/example-stadium.md).

## Capabilities

| Capability | Description |
|------------|-------------|
| Spend ledger | Budget line items, funds received from the public body, and every spend entry with its ACB reference. |
| Reference lookup | Public lookup of any ACB reference. Suppliers and workers can confirm or dispute their own entries. |
| Community observations | Trained community watchdogs record what they see on site, such as worker numbers and stage of construction, so spending can be compared with physical progress. |
| Public data collection | Published tender notices, awards and audit findings are collected, linked per contract and archived. |
| Risk flags | Published, versioned indicators such as unaccounted funds, disputed entries, newly registered payees and spending ahead of progress. Named parties have a right of reply. |
| Blockchain anchoring | Summary hashes of all records are anchored to a public blockchain, so later changes or deletions can be proven. |
| Public portal | All information is published on the Glass Pipe portal, with machine-readable downloads for researchers, journalists and oversight bodies. |

## Design principles

- **Independence.** The platform is not part of any government approval process, and no funder, public body or contractor may control what it publishes.
- **Provenance.** Every published fact links to its source.
- **Fairness.** A flag is an indicator for review, not a finding of wrongdoing. Every flag explains its method and the facts behind it, and named parties may reply publicly. See the [Flags rules](docs/domains/flags/rules.md).
- **Privacy.** Personal information is never written to a blockchain, in any form. Wages are published only as totals per pay period, and watchdog identities are never disclosed. See [ADR-003](docs/architecture/decision-records/ADR-003-personal-information-off-chain.md).
- **Openness.** All core code is MIT licensed and published as a digital public good. Grant funding is used only for development, security, legal review and community onboarding.

## Limitations

- The spend ledger reflects what the contractor records. Funds received but not recorded appear as an **unaccounted balance** rather than being hidden.
- The platform cannot stop a payment or establish that a crime occurred. Its purpose is to make irregularities visible early, so that communities, journalists, councils and oversight bodies can act.
- The threats the system is designed to resist, and those it cannot address, are set out in the [threat model](docs/architecture/security.md).

## Roadmap

| Phase | Scope |
|-------|-------|
| 0. Concept (current) | Documentation, decision records and threat model |
| 1. Prototype | Spend ledger, ACB references and public portal, demonstrated with the stadium example |
| 2. Pilot project | One real project with a participating contractor and community watchdogs |
| 3. Public data flags | Risk flags across a province's published tender data |
| 4. Scale | Additional projects and provinces, optional bank feeds and PAIA request tracking |

The reasoning behind this sequence is recorded in [ADR-006](docs/architecture/decision-records/ADR-006-phased-rollout-independent.md).

## Documentation

The project follows a documentation-first approach. The documentation is the source of truth, and code is built from it.

| Document | Purpose |
|----------|---------|
| [Documentation index](docs/README.md) | Entry point to all project documentation |
| [Overview](docs/context/overview.md) | Problem, stakeholders, scope, success measures and open questions |
| [Village stadium example](docs/context/example-stadium.md) | The spend ledger applied to a R10,000,000 tender |
| [Architecture](docs/architecture/architecture.md) | Components, data flow and data storage |
| [Threat model](docs/architecture/security.md) | Threats, controls and known limitations |
| [Decision records](docs/architecture/decision-records/) | Recorded architecture and product decisions |
| Domain rules | [Spend ledger](docs/domains/spend/rules.md), [Sources](docs/domains/sources/rules.md), [Tenders](docs/domains/tenders/rules.md), [Evidence](docs/domains/evidence/rules.md), [Flags](docs/domains/flags/rules.md), [Disclosure](docs/domains/disclosure/rules.md) |

## Contributing

Contributions are welcome from developers, security reviewers, construction and procurement professionals, legal experts, data specialists, journalists and community organisations.

Please read the [Contributing guide](CONTRIBUTING.md) before opening an issue or pull request. It covers the documentation-first workflow, writing standards, decision records, Rule IDs and review requirements.

## Security

Please report vulnerabilities privately, following the process in [SECURITY.md](SECURITY.md). Do not open public issues for security vulnerabilities.

## Licence

The ACB System is released under the [MIT Licence](LICENSE), so that governments, civil society organisations and others can deploy, adapt and mirror it freely.

## Contact

- Repository: [github.com/Oliesta/acb-system](https://github.com/Oliesta/acb-system)
- Email: oliestao@gmail.com
