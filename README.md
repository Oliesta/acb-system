# ACB System (Anti-Corruption Blockchain System)

> **Status:** 🔬 Concept stage. Documentation first, no code yet.
> **Maintainer:** [@Oliesta](https://github.com/Oliesta)
> **License:** MIT

## 🇿🇦 Every Rand of a tender, visible to the public

When a tender is awarded, the public sees the award value at best. How the contractor spends the money stays hidden. The SIU can only investigate once the funds are already gone.

The **ACB System** is an **independent, open-source transparency platform** that makes the use of tender funds visible while the project runs. Each tender gets a **spend ledger**: the budget split into line items, with every purchase and salary recorded against a line. Each entry gets a unique **ACB reference** that is printed on the invoice. Anyone holding that invoice or payslip can check it was recorded honestly. The community helps flag anything that does not add up.

The ACB System **does not manage, hold or approve any funds**. Money moves through normal bank accounts. The ledger is a tamper-evident mirror of how it was used. See [ADR-005](docs/architecture/decision-records/ADR-005-independent-transparency-platform.md) and [ADR-007](docs/architecture/decision-records/ADR-007-tender-spend-ledger.md).

---

## 🏟️ Example: a R10,000,000 village stadium

| Line item | Budget |
|-----------|--------|
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

The contractor orders 2,000 bags of cement for R190,000. The entry is recorded against "Construction materials", and the ledger issues **`ACB-2026-STD01-000123`**. The supplier prints that reference on their invoice. Anyone can look it up on the portal. If the real invoice was only R90,000, the supplier can dispute it, and the entry is flagged for everyone to see.

Full walkthrough: [village stadium example](docs/context/example-stadium.md).

---

## 🚀 What it does

| | |
|---|---|
| **📒 Spend ledger** | Budget lines from the contract, funds received, and every spend entry with its ACB reference. |
| **🔎 Reference lookup** | Anyone can check an ACB reference. Suppliers and workers can confirm or dispute their own entries. |
| **👀 Community observations** | Trained watchdogs report what they see on site, such as worker counts and stage of work, so spending can be compared with real progress. |
| **📥 Public data** | Published tender notices, awards and audit findings are collected and linked, with a snapshot of every document. |
| **🚩 Flags** | Irregularities are highlighted, for example unaccounted funds, inflated entries, very new payee companies, or spending far ahead of progress. Named parties can reply. |
| **⛓️ Blockchain anchoring** | Summary hashes of every record are anchored to a public blockchain, so nobody can quietly change or delete history. |
| **🪟 Glass Pipe portal** | Everything is public, with open data downloads for journalists, researchers and oversight bodies. |

---

## ⚖️ Fair by design

A flag is a reason to look closer, **never** a finding of wrongdoing. Every flag links to the facts behind it and its published method, and any named contractor or public body can reply publicly. See the [Flags rules](docs/domains/flags/rules.md).

## 🔐 Privacy by design

Personal information is **never** written to a blockchain, not even as a hash. Wages are published only as totals per pay period, while each worker gets a private reference to check their own pay. Watchdog identities are never published. See [ADR-003](docs/architecture/decision-records/ADR-003-personal-information-off-chain.md).

## 🛡️ Honest about limits

The ledger only shows what the contractor records, so money they do not record appears as an **unaccounted balance**. The platform cannot stop a payment or prove a crime. It makes problems visible early, so the community, journalists and oversight bodies such as the SIU can act before the money is gone. See the [threat model](docs/architecture/security.md).

---

## 🗺️ Roadmap

| Phase | Scope |
|-------|-------|
| **0. Concept** (now) | Documentation, decisions, threat model |
| **1. Prototype** | Spend ledger, ACB references and portal, demonstrated with the stadium example |
| **2. Pilot project** | One real project with a participating contractor and community watchdogs |
| **3. Public data flags** | Flags over a whole province's published tender data |
| **4. Scale** | More projects and provinces, optional bank feeds, PAIA request tracking |

Why this order: [ADR-006](docs/architecture/decision-records/ADR-006-phased-rollout-independent.md).

---

## 📚 Documentation

This project is **documentation first**. The docs are the source of truth, and code is built from them. Start at the [documentation index](docs/README.md).

- [Overview](docs/context/overview.md): problem, stakeholders, goals, non-goals and open questions
- [Village stadium example](docs/context/example-stadium.md)
- [Architecture](docs/architecture/architecture.md) and [threat model](docs/architecture/security.md)
- [Decision records](docs/architecture/decision-records/)
- Domain rules: [Spend ledger](docs/domains/spend/rules.md), [Sources](docs/domains/sources/rules.md), [Tenders](docs/domains/tenders/rules.md), [Evidence](docs/domains/evidence/rules.md), [Flags](docs/domains/flags/rules.md), [Disclosure](docs/domains/disclosure/rules.md)

---

## 🏛️ Public benefit

* **Digital public good:** all core code is MIT licensed and stays free for the South African public.
* **Independent:** no funder, public body or contractor may control what is published.
* **No private profit:** grants are used only for development, security, legal review and community onboarding. Any surplus is reinvested in the project.

---

## 🤝 How to contribute

We welcome **developers, data people, quantity surveyors, journalists, legal experts and community members**.

- **Everyone:** read the [Overview](docs/context/overview.md) and pick an open question, or open an issue.
- **Developers and security reviewers:** challenge the [architecture](docs/architecture/architecture.md) and [threat model](docs/architecture/security.md). Every change starts with a doc update, see [how to change anything](docs/README.md#how-to-change-anything).
- **Construction and procurement experts:** help shape budget lines and test the [flag definitions](docs/domains/flags/rules.md).
- **Legal experts:** help with defamation, POPIA and PAIA questions.
- **Community members:** the watchdog programme is described in the [Evidence rules](docs/domains/evidence/rules.md).

---

## 🔒 Security

Please report vulnerabilities privately, as described in [SECURITY.md](SECURITY.md).

## 📜 License

Licensed under the [MIT License](LICENSE), so anyone can deploy, adapt and mirror the platform.

## 📬 Contact

- **GitHub:** [github.com/Oliesta/acb-system](https://github.com/Oliesta/acb-system)
- **Email:** oliestao@gmail.com

---

<p align="center">
  <strong>Build the Glass Pipe. Let everyone see where the money goes.</strong>
</p>
