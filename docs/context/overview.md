# Overview

## Problem

Procurement corruption in South Africa is mostly found after the money is gone. Investigations by the Special Investigating Unit (SIU) and the Auditor-General happen months or years after payment. By then, recovery is slow and rare.

Corruption usually needs one or more of these conditions:

- **Opacity:** the public cannot see what was bought, from whom, or at what price.
- **Unverified delivery:** payment is made on paperwork alone, not on proof that work was done.
- **Single points of control:** one official can approve a payment or change a budget.
- **Mutable records:** documents can go missing or be changed after the fact.
- **Ineligible suppliers:** payments reach suppliers that are not registered or not tax compliant.

## What the ACB System is

The ACB System is an open-source **evidence and approval layer** for public contracts. It sits beside a public body's existing financial system and does four things:

1. Records each contract and its milestones in a tamper-evident ledger.
2. Collects independent evidence that each milestone was delivered.
3. Acts as a **payment release gate**: a milestone payment is only authorised when the evidence and approval rules are met.
4. Publishes what was paid, for what, and on what evidence, on a public portal (the "Glass Pipe").

## What the ACB System is not

- It is **not** a wallet or custodian of public money. Funds stay in government bank accounts and move through existing payment systems. See [ADR-001](../architecture/decision-records/ADR-001-funds-stay-on-government-rails.md).
- It is **not** a cryptocurrency or token project.
- It does **not** replace the procurement process, bid committees or the Auditor-General. It makes their work easier to check.
- It does **not** prove that a contract was fairly awarded. It proves what happened after award, and makes award data public.
- It does **not** store personal information on a blockchain. See [ADR-003](../architecture/decision-records/ADR-003-personal-information-off-chain.md).

## Who it is for

| Stakeholder | What they get | What they must do |
|-------------|---------------|-------------------|
| Public bodies (departments, municipalities, SOEs) | Cleaner audits, fewer irregular expenditure findings, a defensible record for every payment | Register contracts and milestones, connect the payment gate to their financial system |
| Contractors | Faster, more predictable payment once evidence is accepted | Submit milestone claims with invoices |
| Inspectors and engineers | A clear, recorded basis for sign-off that protects them from pressure | Submit inspection evidence through the mobile app |
| Community watchdogs | A safe way to report what they see on site | Follow the [watchdog rules](../domains/evidence/rules.md) |
| Citizens, journalists, researchers | Open data on public spending | Nothing. Read access is public |
| Oversight bodies (AGSA, SIU, Public Protector) | A complete, tamper-evident trail per contract | Nothing. Read access is public, with extra access by agreement |

Contractor benefit matters. Honest contractors are often paid late. If the system shortens the time from verified delivery to payment, contractors have a reason to want it.

## Phased plan

Details and reasoning are in [ADR-004](../architecture/decision-records/ADR-004-phased-rollout.md).

| Phase | Scope | Needs government integration? |
|-------|-------|-------------------------------|
| 0. Concept | Docs, ADRs, threat model | No |
| 1. Transparency | Public portal over already published tender and award data, anchored to a public chain | No |
| 2. Evidence | Milestone verification on a pilot project, ideally donor or NGO funded | No, only the pilot funder |
| 3. Payment gate | Gate connected to one partner public body's financial system | Yes, one partner |
| 4. Scale | More public bodies, more data sources | Yes |

## Success measures

Targets are proposed and MUST be confirmed before the Phase 2 pilot starts.

| Measure | Proposed target |
|---------|-----------------|
| Share of pilot contract value with every payment traced to accepted evidence | 100% |
| Median days from milestone claim to verification decision | 10 working days or fewer |
| Median days from accepted evidence to payment | Within the 30-day payment requirement in Treasury Regulations |
| Payments released without meeting gate rules | 0 |
| Personal information found on-chain or on the public portal | 0 |

## Legal context

The system must work within, not around, these laws:

- Public Finance Management Act, 1999 (PFMA) and Treasury Regulations
- Municipal Finance Management Act, 2003 (MFMA)
- Preferential Procurement Policy Framework Act, 2000 (PPPFA)
- Public Procurement Act, 2024, once in force
- Protection of Personal Information Act, 2013 (POPIA)
- Protected Disclosures Act, 2000, for people who report wrongdoing

## Open questions

These are owned by the maintainer and MUST be answered before the phase named.

| # | Question | Needed before |
|---|----------|---------------|
| Q1 | What is a sourced, citable figure for annual procurement losses? The previous README figure had no source and was removed. | Any public pitch |
| Q2 | Does the eTender Publication Portal provide machine-readable award data (for example OCDS) that Phase 1 can use? | Phase 1 |
| Q3 | Which public chain do we anchor to? See [ADR-002](../architecture/decision-records/ADR-002-public-chain-anchoring.md). | Phase 1 |
| Q4 | Who is the Phase 2 pilot funder and project? | Phase 2 |
| Q5 | Can CSD supplier status be checked by API, and under what agreement? | Phase 3 |
| Q6 | Which legal entity will hold data, sign agreements and receive grants, now that there is no lead company? | Phase 2 |
