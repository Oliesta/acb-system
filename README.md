# ACB System (Anti-Corruption Blockchain System)

> **Status:** 🔬 Concept stage. Documentation first, no code yet.
> **Maintainer:** [@Oliesta](https://github.com/Oliesta)
> **License:** MIT

## 🇿🇦 Let everyone see where the money goes

Procurement corruption in South Africa is mostly found after the money is gone. Part of the reason is that the information is scattered, unlinked, easy to change and never checked against what is actually built.

The **ACB System** is an **independent, open-source transparency platform** for public procurement. It brings published tender data and community observations together in one place, highlights what deserves a closer look, and makes sure nobody can quietly rewrite the record.

It does **not** approve or block payments and has no role in government processes. It works without any public body's cooperation. See [ADR-005](docs/architecture/decision-records/ADR-005-independent-transparency-platform.md).

---

## 🚀 What it does

| | |
|---|---|
| **📥 Collect** | Gathers published tender notices, awards, budgets and audit findings from public sources, and keeps a snapshot of every document. |
| **🔗 Link** | Builds one public record per contract: notice, award, variations, deliverables and completion, with a source for every fact. |
| **👀 Observe** | Trained community watchdogs report what they see on project sites, through a mobile app built for their safety. |
| **🚩 Flag** | Highlights risk indicators, such as unadvertised awards or very new suppliers, using published methods. Named parties can reply. |
| **🪟 Publish** | Shows it all on the **Glass Pipe** portal, with open data downloads for journalists, researchers and oversight bodies. |
| **⛓️ Anchor** | Anchors summary hashes of the record to a public blockchain, so any later change or deletion can be proven. |

---

## ⚖️ Fair by design

A flag is a reason to look closer, **never** a finding of wrongdoing. Every flag links to the facts behind it and its published method, and any named supplier or public body can reply publicly. See the [Flags rules](docs/domains/flags/rules.md).

## 🔐 Privacy by design

Personal information is **never** written to a blockchain, not even as a hash. Watchdog identities are never published. See [ADR-003](docs/architecture/decision-records/ADR-003-personal-information-off-chain.md).

## 🛡️ Honest about limits

The platform cannot stop a payment or prove a crime. It makes problems visible early, so citizens, journalists and oversight bodies can act. The [threat model](docs/architecture/security.md) covers false reports, watchdog safety, takedown pressure and tampering.

---

## 🗺️ Roadmap

| Phase | Scope |
|-------|-------|
| **0. Concept** (now) | Documentation, decisions, threat model |
| **1. Open data portal** | Published tender and award data for one province, linked and anchored |
| **2. Flags** | Risk indicators with a right of reply |
| **3. Community observations** | Watchdogs in one pilot area |
| **4. Scale** | More provinces, more sources, PAIA request tracking |

Why this order: [ADR-006](docs/architecture/decision-records/ADR-006-phased-rollout-independent.md).

---

## 📚 Documentation

This project is **documentation first**. The docs are the source of truth, and code is built from them. Start at the [documentation index](docs/README.md).

- [Overview](docs/context/overview.md): problem, stakeholders, goals, non-goals and open questions
- [Architecture](docs/architecture/architecture.md): components and data flow
- [Security and threat model](docs/architecture/security.md)
- [Decision records](docs/architecture/decision-records/)
- Domain rules: [Sources](docs/domains/sources/rules.md), [Tenders](docs/domains/tenders/rules.md), [Evidence](docs/domains/evidence/rules.md), [Flags](docs/domains/flags/rules.md), [Disclosure](docs/domains/disclosure/rules.md)

---

## 🏛️ Public benefit

* **Digital public good:** all core code is MIT licensed and stays free for the South African public.
* **Independent:** no funder, public body or supplier may control what is published.
* **No private profit:** grants are used only for development, security, legal review and community onboarding. Any surplus is reinvested in the project.

---

## 🤝 How to contribute

We welcome **developers, data people, journalists, legal experts and community members**.

- **Everyone:** read the [Overview](docs/context/overview.md) and pick an open question, or open an issue.
- **Developers and security reviewers:** challenge the [architecture](docs/architecture/architecture.md) and [threat model](docs/architecture/security.md). Every change starts with a doc update, see [how to change anything](docs/README.md#how-to-change-anything).
- **Data and procurement experts:** help find sources and test the [flag definitions](docs/domains/flags/rules.md).
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
