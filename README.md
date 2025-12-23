# ACB System (Anti-Corruption Blockchain System)

## 🇿🇦 Restoring Trust in Public Procurement

The **ACB System** is an open-source, decentralized framework designed to eliminate corruption in the South African public sector. By shifting from **reactive** investigations (SIU post-mortems) to **real-time** prevention, we ensure that every Rand allocated to a tender is trackable, verified, and used for its intended purpose.

---

## 🚀 Core Features

* **Milestone-Based Escrow:** Tender funds are locked in smart contracts and only released in tranches upon verified physical progress.
* **The "Glass Pipe" Ledger:** A public transparency portal where citizens can track fund utilization in real-time, down to individual line items.
* **Immutable Invoice Vault:** Invoices are hashed and stored on **IPFS**, preventing "lost" documents or retroactive tampering.
* **Triple-Entry Accounting:** Every transaction is reconciled between the Government, the Contractor, and the Blockchain simultaneously.
* **Automated Verification (Oracles):** Integration with the **National Treasury CSD** (Central Supplier Database) to ensure funds only reach verified, tax-compliant entities.
* **Multi-Signature Governance:** Prevents single-point-of-failure corruption by requiring multiple independent authorizations for budget changes.

---

## 📂 Repository Structure

```text
acb-system/
│── contracts/           # Smart contracts (Solidity/Rust) for Escrow & Milestones
│── backend/             # Node.js/Python API for OCR, logic, and database management
│── frontend/            # Web Dashboard (v0.dev/Next.js) for public transparency
│── mobile/              # React Native/Flutter app for site inspections & PoD
│── oracles/             # Integration scripts for CSD, SARS, and GPS data
│── storage/             # IPFS/Filecoin logic for tamper-proof invoice hosting
│── governance/          # Multi-sig and voting logic for budget adjustments
│── docs/                # Whitepaper, API docs, and Setup Guide
│── tests/               # Security audits and integration test suites
│── scripts/             # One-click deployment (Hardhat/Foundry)
│── .github/             # CI/CD pipelines and automated security scanning
│── README.md            # The "Face" of the project
└── LICENSE              # MIT License (Open Source)

```

---

## 🛠️ Getting Started

### Prerequisites

* **Blockchain:** Hardhat / Foundry (Development)
* **Backend:** Node.js v18+ or Python 3.10+
* **Storage:** IPFS Node or Pinata API Key
* **Database:** PostgreSQL (for metadata)

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

```


3. **Configure Backend:**
```bash
cd ../backend
npm install
cp .env.example .env # Update with your CSD API keys and RPC URL
npm run dev

```


4. **Launch Public Portal:**
```bash
cd ../frontend
npm install
npm run dev

```



---

## 🤝 Contribution Guidelines

We welcome developers, auditors, and legal experts to help build this "Trust Layer" for South Africa.

1. **Fork** the project.
2. Create a **Feature Branch** (`git checkout -b feature/AntiFraudLogic`).
3. **Commit** your changes (`git commit -m 'Add OCR validation logic'`).
4. **Push** to the branch (`git push origin feature/AntiFraudLogic`).
5. Open a **Pull Request**.

---

## 📜 License

This project is licensed under the **MIT License** - see the [LICENSE](https://www.google.com/search?q=LICENSE) file for details.

---
