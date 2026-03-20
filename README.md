---

# ACB System (Anti-Corruption Blockchain System)

> **Status:** 🔬 Pre-Alpha - Active Development
> **Lead Developer:** REVOICE AI (Pty) Ltd (Reg: 2025/409722/07)

## 🇿🇦 Restoring Trust in Public Procurement

The **ACB System** is an open-source, decentralized framework designed to eliminate corruption in the South African public sector. By shifting from **reactive** investigations (SIU post-mortems) to **real-time** prevention, we ensure that every Rand allocated to a tender is trackable, verified, and used for its intended purpose.

South Africa loses an estimated **R25–30 billion annually** to procurement corruption. The ACB System makes corruption not just detectable - but structurally impossible.

---

## 🏛️ Project Governance & Public Benefit

While developed by **REVOICE AI (Pty) Ltd**, the ACB System is operated as a **Public Benefit Activity**. 

* **Digital Public Good:** All core code is licensed under the MIT License to ensure it remains a permanent, free asset for the South African public.
* **Fiduciary Oversight:** All grant funding is ring-fenced and utilized strictly for technical development, security auditing, and community onboarding. 
* **Non-Inurement:** REVOICE AI (Pty) Ltd commits to a zero-dividend policy regarding project-specific grants; all surpluses are reinvested into the protocol's security and reach.

---

## 🚀 Core Features

* **Milestone-Based Escrow:** Tender funds are locked in smart contracts and only released in tranches upon verified physical progress.
* **The "Glass Pipe" Ledger:** A public transparency portal where citizens can track fund utilisation in real-time, down to individual line items.
* **Immutable Invoice Vault:** Invoices are hashed and stored on **IPFS**, preventing "lost" documents or retroactive tampering.
* **Triple-Entry Accounting:** Every transaction is reconciled between the Government, the Contractor, and the Blockchain simultaneously.
* **Automated Verification (Oracles):** Integration with the **National Treasury CSD** (Central Supplier Database) and **SARS** to ensure funds only reach verified, tax-compliant entities.
* **Multi-Signature Governance:** Prevents single-point-of-failure corruption by requiring multiple independent authorisations for budget changes and fund releases.

---

## 🔐 Data Privacy & POPIA Compliance

The ACB System is designed with South Africa's **Protection of Personal Information Act (POPIA)** at its core:

| Data Type | Storage | Visibility |
|-----------|---------|------------|
| Contractor PII (names, IDs, banking) | **Off-chain** - encrypted PostgreSQL | Private, access-controlled |
| Transaction hashes & amounts | **On-chain** - Polygon/Base | Public, anonymised |
| Invoices & proof-of-delivery | **IPFS** - content-addressed | Public (redacted PII) |
| Verification metadata (GPS, timestamps) | **Off-chain** with on-chain hash | Hash public, data private |

**Key principles:**
- Personal information is **never** stored on the blockchain.
- All on-chain data is anonymised or hashed.
- Data subject access requests are supported via the admin API.
- Full POPIA compliance audit will be conducted before pilot launch.

---

## 📂 Repository Structure

```text
acb-system/
├── contracts/         # Smart contracts (Solidity) for Escrow & Milestones
├── backend/           # Node.js/Python API for OCR, logic, and database management
├── frontend/          # Web Dashboard (Next.js) for public transparency
├── mobile/            # React Native app for site inspections & proof-of-delivery
├── oracles/           # Integration scripts for CSD, SARS, and GPS validation
├── storage/           # IPFS/Filecoin logic for tamper-proof invoice hosting
├── governance/        # Multi-sig constitution and non-inurement undertakings
│   └── CONSTITUTION.md 
├── docs/              # Whitepaper, POPIA framework, and Setup Guide
├── SECURITY.md        # Responsible disclosure policy
├── README.md
└── LICENSE
```

---

## 🛡️ Security & Auditing

This system is designed to handle public funds. Security is non-negotiable.

* **Smart contract audits:** All contracts must pass at least two independent security audits before mainnet deployment.
* **Upgradeable proxy pattern:** Contracts use time-locked governance for upgrades - no single key can modify the system.
* **CI/CD security scanning:** Automated vulnerability scanning on every pull request.

---

## 🤝 How to Contribute

We welcome **developers, auditors, legal experts, and community members** to help build this Trust Layer for South Africa.

### For Community Watchdogs (Non-Technical)
You don't need to code to fight corruption. The **Community Watchdog Programme** trains citizens to:
- Conduct site inspections and upload geo-tagged proof-of-delivery evidence.
- Verify that physical progress matches reported milestones.
- Flag discrepancies between invoices and actual deliverables.
- **Interested?** See [`docs/watchdog-programme.md`](docs/watchdog-programme.md).

---

## 📜 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details. This ensures the project remains a **Digital Public Good**, allowing governments and NGOs to deploy and fork the system freely to maximize social impact.

---

## 📬 Contact

- **GitHub:** [github.com/Oliesta/acb-system](https://github.com/Oliesta/acb-system)
- **Email:** oliestao@gmail.com
- **Lead Organization:** REVOICE AI (Pty) Ltd, South Africa

---

<p align="center">
  <strong>Build the Glass Pipe. Let everyone see where the money goes.</strong>
</p>

---
