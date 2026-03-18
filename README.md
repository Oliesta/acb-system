# ACB System (Anti-Corruption Blockchain System)

> **Status:** 🔬 Pre-Alpha — Active Development

## 🇿🇦 Restoring Trust in Public Procurement

The **ACB System** is an open-source, decentralized framework designed to eliminate corruption in the South African public sector. By shifting from **reactive** investigations (SIU post-mortems) to **real-time** prevention, we ensure that every Rand allocated to a tender is trackable, verified, and used for its intended purpose.

South Africa loses an estimated **R25–30 billion annually** to procurement corruption ([SmartProcurement](https://smartprocurement.co.za)). The ACB System makes corruption not just detectable — but structurally impossible.

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
| Contractor PII (names, IDs, banking) | **Off-chain** — encrypted PostgreSQL | Private, access-controlled |
| Transaction hashes & amounts | **On-chain** — Polygon/Base | Public, anonymised |
| Invoices & proof-of-delivery | **IPFS** — content-addressed | Public (redacted PII) |
| Verification metadata (GPS, timestamps) | **Off-chain** with on-chain hash | Hash public, data private |

**Key principles:**
- Personal information is **never** stored on the blockchain
- All on-chain data is anonymised or hashed
- An appointed **Information Officer** oversees compliance
- Data subject access requests are supported via the admin API
- Full POPIA compliance audit will be conducted before pilot launch

> ⚠️ **SARB Disclaimer:** The stablecoin escrow component is subject to evolving South African Reserve Bank regulation. The pilot phase will use a simulated token on testnet rather than a live stablecoin until regulatory clarity is achieved.

---

## 📂 Repository Structure

```text
acb-system/
├── contracts/           # Smart contracts (Solidity) for Escrow & Milestones
├── backend/             # Node.js/Python API for OCR, logic, and database management
├── frontend/            # Web Dashboard (Next.js) for public transparency
├── mobile/              # React Native app for site inspections & proof-of-delivery
├── oracles/             # Integration scripts for CSD, SARS, and GPS validation
├── storage/             # IPFS/Filecoin logic for tamper-proof invoice hosting
├── governance/          # Multi-sig constitution, voting logic, upgrade procedures
│   └── CONSTITUTION.md  # Protocol governance rules and amendment process
├── docs/                # Whitepaper, API docs, and Setup Guide
├── tests/               # Security audits and integration test suites
├── scripts/             # One-click deployment (Hardhat/Foundry)
├── .github/             # CI/CD pipelines and automated security scanning
├── SECURITY.md          # Responsible disclosure policy
├── README.md
└── LICENSE
```

---

## 🛠️ Getting Started

### Prerequisites

* **Blockchain:** Hardhat / Foundry (Development)
* **Backend:** Node.js v18+ or Python 3.10+
* **Storage:** IPFS Node or Pinata API Key
* **Database:** PostgreSQL 14+ (for off-chain metadata)

### Installation

1. **Clone the repository:**
```bash
git clone https://github.com/Oliesta/acb-system.git
cd acb-system
```

2. **Setup Smart Contracts:**
```bash
cd contracts
npm install
npx hardhat compile
npx hardhat test  # Run contract test suite
```

3. **Configure Backend:**
```bash
cd ../backend
npm install
cp .env.example .env  # Update with your CSD API keys and RPC URL
npm run dev
```

4. **Launch Public Portal:**
```bash
cd ../frontend
npm install
npm run dev
```

5. **Run Mobile App (for site inspectors):**
```bash
cd ../mobile
npm install
npx expo start
```

---

## 🛡️ Security

This system is designed to handle public funds. Security is non-negotiable.

* **Smart contract audits:** All contracts must pass at least two independent security audits before mainnet deployment
* **Bug bounty programme:** See [SECURITY.md](SECURITY.md) for our responsible disclosure policy and bounty tiers
* **Upgradeable proxy pattern:** Contracts use time-locked governance for upgrades — no single key can modify the system
* **CI/CD security scanning:** Automated vulnerability scanning on every pull request

If you discover a vulnerability, **do not open a public issue.** Follow the process in [SECURITY.md](SECURITY.md).

---

## 🤝 How to Contribute

We welcome **developers, auditors, legal experts, and community members** to help build this Trust Layer for South Africa.

### For Developers & Auditors

1. **Fork** the project
2. Create a **Feature Branch** (`git checkout -b feature/AntiFraudLogic`)
3. **Commit** your changes (`git commit -m 'Add OCR validation logic'`)
4. **Push** to the branch (`git push origin feature/AntiFraudLogic`)
5. Open a **Pull Request**

All smart contract changes require security review before merge.

### For Community Watchdogs (Non-Technical)

You don't need to code to fight corruption. The **Community Watchdog Programme** trains citizens to:

- Conduct site inspections and upload geo-tagged proof-of-delivery evidence
- Verify that physical progress matches reported milestones
- Flag discrepancies between invoices and actual deliverables

**Interested?** See [`docs/watchdog-programme.md`](docs/watchdog-programme.md) for the training guide and onboarding process.

### For Legal & Policy Experts

- Review and improve our POPIA compliance framework
- Contribute to the proposed **ACB Act** drafting
- Advise on SARB regulatory positioning for the escrow mechanism

---

## 🗺️ Roadmap

| Phase | Timeline | Key Deliverables |
|-------|----------|------------------|
| **Phase 1** | Q1–Q2 (Year 1) | Open-source repo, mock tender on testnet, grant applications, whitepaper |
| **Phase 2** | Q3 (Year 1) | Pilot with clean-audit municipality, CSD oracle integration, Watchdog onboarding |
| **Phase 3** | Q4 (Year 1) | Public dashboard launch, citizen tracking, media engagement |
| **Phase 4** | Year 2 | Lobby for ACB Act, expand to 3–5 municipalities, audit firm partnerships |
| **Phase 5** | Year 3+ | National rollout, provincial treasury integration, international replication |

---

## ⚖️ Governance

The ACB System uses **multi-signature governance** to prevent any single party from controlling the system. Protocol changes, budget adjustments, and contract upgrades require approval from multiple independent signatories.

See [`governance/CONSTITUTION.md`](governance/CONSTITUTION.md) for:
- The multi-sig structure and signatory roles
- Voting thresholds for different decision types
- The amendment process for protocol changes
- Emergency procedures and safeguards

---

## 📜 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

> **Note on license choice:** MIT was chosen to maximise adoption and allow governments, NGOs, and other NPOs to deploy freely. Contributors should be aware that this permits commercial forks without contribution-back obligations. If this becomes a concern as the project matures, migration to AGPL-3.0 may be proposed through the governance process.

---

## 📬 Contact

- **GitHub:** [github.com/Oliesta/acb-system](https://github.com/Oliesta/acb-system)
- **Email:** oliestao@gmail.com
- **Organisation:** ACB System NPO, South Africa

---

<p align="center">
  <strong>Build the Glass Pipe. Let everyone see where the money goes.</strong>
</p>
