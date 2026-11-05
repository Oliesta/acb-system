# ACB System (Anti-Corruption Blockchain System)

> **Status:** 🔬 Concept stage. Documentation first, no code yet.
> **Maintainer:** [@Oliesta](https://github.com/Oliesta)
> **License:** MIT

## 🇿🇦 No proof, no payment

Procurement corruption in South Africa is mostly found after the money is gone. The **ACB System** is an open-source evidence and approval layer for public contracts that aims to stop bad payments before they happen.

The idea is simple: **a milestone is only paid when independent evidence shows it was delivered, and people in separate roles approve the release.** Every step is recorded in a tamper-evident ledger and shown on a public portal, the **Glass Pipe**.

The system does **not** hold public money. Funds stay in government bank accounts and move through existing payment systems. The ACB System decides whether a payment may be authorised and makes that decision public. See [ADR-001](docs/architecture/decision-records/ADR-001-funds-stay-on-government-rails.md).

---

## 🚀 How it works

| Step | What happens |
|------|--------------|
| **1. Register** | The contract, supplier (by CSD number) and milestones are recorded. Award data goes public. |
| **2. Claim** | The supplier claims a milestone and uploads the invoice. |
| **3. Verify** | Inspectors, assigned at random, check the site and submit evidence from a mobile app. Community watchdogs can report what they see. |
| **4. Gate** | The system checks the evidence, the supplier's CSD and tax status, and looks for duplicate invoices. |
| **5. Approve** | At least two approvers in separate roles sign the release. The inspector cannot be one of them. |
| **6. Pay** | The public body pays through its normal systems and sends back the payment reference. |
| **7. Publish** | Every step appears on the Glass Pipe portal. Batches of records are anchored to a public blockchain so nobody can quietly rewrite history. |

---

## 🔐 Privacy by design

Personal information is **never** written to a blockchain, not even as a hash. Only batch summary hashes go on-chain. Personal data is encrypted off-chain so POPIA correction and deletion rights can be honoured. See [ADR-003](docs/architecture/decision-records/ADR-003-personal-information-off-chain.md).

---

## 🛡️ Honest about limits

The biggest threat is people inside the process working together, not outside hackers. The [threat model](docs/architecture/security.md) explains how random inspector assignment, separated roles and public flags make collusion harder, and lists what the system **cannot** stop, such as a rigged award.

---

## 🗺️ Roadmap

| Phase | Scope |
|-------|-------|
| **0. Concept** (now) | Documentation, decisions, threat model |
| **1. Transparency** | Public portal over already published tender and award data |
| **2. Evidence** | Milestone verification on one pilot project, ideally donor or NGO funded |
| **3. Payment gate** | Gate connected to one partner public body's financial system |
| **4. Scale** | More public bodies and data sources |

Why this order: [ADR-004](docs/architecture/decision-records/ADR-004-phased-rollout.md).

---

## 📚 Documentation

This project is **documentation first**. The docs are the source of truth, and code is built from them.

Start at the [documentation index](docs/README.md). Key pages:

- [Overview](docs/context/overview.md): problem, stakeholders, goals, non-goals and open questions
- [Architecture](docs/architecture/architecture.md): components and the flow of one payment
- [Security and threat model](docs/architecture/security.md)
- [Decision records](docs/architecture/decision-records/)
- Domain rules: [Tenders](docs/domains/tenders/rules.md), [Milestones](docs/domains/milestones/rules.md), [Evidence](docs/domains/evidence/rules.md), [Payments](docs/domains/payments/rules.md), [Disclosure](docs/domains/disclosure/rules.md)

---

## 🏛️ Public benefit

The ACB System is a public benefit project, not a commercial product.

* **Digital public good:** all core code is MIT licensed and stays free for the South African public.
* **Ring-fenced funding:** any grant funding is used only for development, security audits and community onboarding.
* **No private profit:** project grants are not distributed as profit. Any surplus is reinvested in the project.

---

## 🤝 How to contribute

We welcome **developers, auditors, legal and procurement experts, and community members**.

- **Everyone:** read the [Overview](docs/context/overview.md) and pick an open question, or open an issue.
- **Developers and security reviewers:** challenge the [architecture](docs/architecture/architecture.md) and [threat model](docs/architecture/security.md). Every change starts with a doc update, see [how to change anything](docs/README.md#how-to-change-anything).
- **Legal and procurement experts:** check the design against the PFMA, MFMA, PPPFA, the Public Procurement Act and POPIA.
- **Community members:** the watchdog programme is described in the [Evidence rules](docs/domains/evidence/rules.md).

---

## 🔒 Security

Please report vulnerabilities privately, as described in [SECURITY.md](SECURITY.md).

---

## 📜 License

Licensed under the [MIT License](LICENSE), so governments, municipalities and NGOs can freely deploy, adapt and fork the system.

---

## 📬 Contact

- **GitHub:** [github.com/Oliesta/acb-system](https://github.com/Oliesta/acb-system)
- **Email:** oliestao@gmail.com

---

<p align="center">
  <strong>No proof, no payment. Let everyone see where the money goes.</strong>
</p>
