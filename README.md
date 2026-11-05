# ACB System (Anti-Corruption Blockchain System)

> **Status:** 🔬 Pre-Alpha – Active Development
> **Maintainer:** [@Oliesta](https://github.com/Oliesta)
> **License:** MIT

## 🇿🇦 Restoring Trust in Public Procurement

The **ACB System** is an open-source, decentralised framework for preventing corruption in South African public procurement. Instead of relying on **reactive** investigations after the money is gone (e.g. SIU post-mortems), it enforces **real-time** controls so that every Rand allocated to a tender is traceable, verified, and spent on its intended purpose.

South Africa loses an estimated **R25–30 billion a year** to procurement corruption. The goal of the ACB System is to make that corruption hard to commit and impossible to hide.

---

## 🏛️ Governance & Public Benefit

The ACB System is run as a **public benefit project**, not a commercial product.

* **Digital Public Good:** All core code is MIT-licensed and will remain a free, permanent asset for the South African public.
* **Ring-fenced funding:** Any grant funding is used strictly for technical development, security audits, and community onboarding.
* **No private profit:** Project-specific grants are not distributed as profit; any surplus is reinvested in the protocol's security and reach.
* **Open governance:** Decisions about the protocol are documented publicly in [`governance/`](governance/).

---

## 🚀 Core Features

| Feature | What it does |
|---------|--------------|
| **Milestone-Based Escrow** | Tender funds are locked in smart contracts and released in tranches only once physical progress is verified. |
| **"Glass Pipe" Ledger** | A public transparency portal where citizens can follow how funds are used, down to individual line items. |
| **Immutable Invoice Vault** | Invoices are hashed and stored on **IPFS**, so documents can't go "missing" or be altered after the fact. |
| **Triple-Entry Accounting** | Every transaction is reconciled between the government, the contractor, and the blockchain at the same time. |
| **Automated Verification (Oracles)** | Checks against the **National Treasury Central Supplier Database (CSD)** and **SARS** ensure payments only reach registered, tax-compliant suppliers. |
| **Multi-Signature Governance** | Budget changes and fund releases need several independent approvals, removing single points of failure. |

---

## 🔐 Data Privacy & POPIA Compliance

The system is designed around South Africa's **Protection of Personal Information Act (POPIA)**:

| Data Type | Storage | Visibility |
|-----------|---------|------------|
| Contractor PII (names, IDs, banking details) | **Off-chain** – encrypted PostgreSQL | Private, access-controlled |
| Transaction hashes & amounts | **On-chain** – Polygon / Base | Public, anonymised |
| Invoices & proof-of-delivery | **IPFS** – content-addressed | Public, with PII redacted |
| Verification metadata (GPS, timestamps) | **Off-chain**, with an on-chain hash | Hash public, data private |

**Key principles**

- Personal information is **never** stored on the blockchain.
- All on-chain data is anonymised or hashed.
- Data subject access requests are handled through the admin API.
- A full POPIA compliance audit will be completed before any pilot launch.

---

## 📂 Repository Structure

The planned layout is below. Most directories are not created yet; they will be added as each component is developed.

```text
acb-system/
├── contracts/         # Solidity smart contracts for escrow and milestones
├── backend/           # API for OCR, business logic, and database access
├── frontend/          # Next.js public transparency dashboard
├── mobile/            # React Native app for site inspections and proof-of-delivery
├── oracles/           # CSD, SARS, and GPS validation integrations
├── storage/           # IPFS/Filecoin logic for tamper-proof invoice storage
├── governance/        # Multi-sig constitution and public benefit commitments
│   └── CONSTITUTION.md
├── docs/              # Whitepaper, POPIA framework, and setup guide
├── SECURITY.md        # Responsible disclosure policy
├── LICENSE
└── README.md
```

---

## 🛡️ Security & Auditing

This system is intended to handle public funds, so security is non-negotiable.

* **Independent audits:** Every smart contract must pass at least two independent security audits before mainnet deployment.
* **Time-locked upgrades:** Contracts use an upgradeable proxy pattern with time-locked, multi-sig governance – no single key can change the system.
* **Automated scanning:** Every pull request is scanned for vulnerabilities in CI.
* **Responsible disclosure:** Please report vulnerabilities privately as described in [`SECURITY.md`](SECURITY.md), not in public issues.

---

## 🤝 How to Contribute

We welcome **developers, auditors, legal experts, and community members** who want to help build a trust layer for South Africa.

### Developers & Auditors
- Browse the open issues, or open one to propose a feature or report a bug.
- Fork the repo, create a feature branch, and open a pull request with a clear description of the change.
- Security reviews of contracts and architecture are especially welcome.

### Legal & Policy Experts
- Help us align the system with the PFMA, MFMA, PPPFA, and POPIA.
- Review governance documents in [`governance/`](governance/).

### Community Watchdogs (Non-Technical)
You don't need to write code to fight corruption. The **Community Watchdog Programme** trains citizens to:
- Inspect project sites and upload geo-tagged proof-of-delivery evidence.
- Check that physical progress matches reported milestones.
- Flag differences between invoices and what was actually delivered.

**Interested?** See [`docs/watchdog-programme.md`](docs/watchdog-programme.md).

---

## 📜 License

Licensed under the **MIT License** – see [LICENSE](LICENSE). This keeps the ACB System a **Digital Public Good** that governments, municipalities, and NGOs can freely deploy, adapt, and fork.

---

## 📬 Contact

- **GitHub:** [github.com/Oliesta/acb-system](https://github.com/Oliesta/acb-system)
- **Email:** oliestao@gmail.com

---

<p align="center">
  <strong>Build the Glass Pipe. Let everyone see where the money goes.</strong>
</p>
