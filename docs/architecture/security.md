# Security and Threat Model

Status: Proposed.

An independent transparency platform will have powerful enemies. The main risks are **contractors recording a false picture of their spending**, **false information getting published**, **people being harmed for reporting**, and **pressure to take content down**.

## Threats and controls

| ID | Threat | Control | Rule |
|----|--------|---------|------|
| T1 | False observations planted to smear a competitor or official | Only verified observations feed flags. Moderation before publication | [EVD-006](../domains/evidence/rules.md), [FLG-005](../domains/flags/rules.md) |
| T2 | Many fake watchdog accounts (Sybil attack) | Watchdogs are trained and onboarded through a community partner, not open sign-up | [Evidence rules](../domains/evidence/rules.md) |
| T3 | Fake or reused photos | In-app capture with time, GPS and hash. Duplicate fingerprints flagged | [EVD-002](../domains/evidence/rules.md), [EVD-003](../domains/evidence/rules.md) |
| T4 | GPS spoofing | GPS is one signal, never proof on its own | [EVD-004](../domains/evidence/rules.md) |
| T5 | Watchdogs identified and threatened | Identity never published. Observations delayed 72 hours and location coarsened. Public places only | [EVD-007](../domains/evidence/rules.md), [DSC-004](../domains/disclosure/rules.md) |
| T6 | Defamation claims over flags | Factual wording, published methods, linked facts, right of reply, visible corrections | [FLG-001 to FLG-008](../domains/flags/rules.md) |
| T7 | Source documents removed to hide evidence | Snapshots of every document, and removal shown as a flag | [SRC-003](../domains/sources/rules.md), [SRC-004](../domains/sources/rules.md) |
| T8 | Operator quietly edits or deletes records | Append-only ledger anchored on-chain. Anyone can verify | [ADR-002](decision-records/ADR-002-public-chain-anchoring.md) |
| T9 | Pressure or capture through funding | No funder may control what is published | [IND-004](decision-records/ADR-005-independent-transparency-platform.md) |
| T10 | Takedown demands or platform shutdown | Takedown process below. Open data downloads and public code let others mirror the platform | [DSC-003](../domains/disclosure/rules.md) |
| T11 | Personal information leaks | No personal information on-chain. Automated scans of public files | [ADR-003](decision-records/ADR-003-personal-information-off-chain.md), [DSC-002](../domains/disclosure/rules.md) |
| T12 | Admin or anchoring keys stolen | Keys in a managed key service. Admin actions need 2 people and are ledger events | To be written before Phase 1 |
| T13 | Contractor records inflated amounts | Payees and workers can look up their reference and dispute it | [SPD-014](../domains/spend/rules.md), [SPD-015](../domains/spend/rules.md), flag F13 |
| T14 | Contractor pays a fake or related company | New company check, payee confirmation, price comparison | Flags F03, F08, F15 |
| T15 | Ghost workers on payroll | Worker counts compared with site observations. Each worker gets a private reference | [SPD-018](../domains/spend/rules.md), flag F14 |
| T16 | Contractor simply does not record spending | Unaccounted balance is public | [SPD-016](../domains/spend/rules.md), flag F10 |
| T17 | One ACB reference reused on several invoices | Every reference is unique, reuse is flagged | [SPD-INV-3](../domains/spend/rules.md) |
| T18 | Contractor account taken over | Entries signed per user, 2-step sign-in, unusual activity alerts | To be written before Phase 2 |

## Takedown process

1. Every takedown or correction demand is logged as a ledger event, without personal information of the requester.
2. Content is only removed if it is wrong, contains personal information, or a court orders it.
3. Removal is shown publicly as "removed" with the reason. Content is never silently deleted.
4. Legal demands go to the operating entity's legal adviser (open question Q6 in the [Overview](../context/overview.md)).

## What the system cannot do

- It cannot stop a payment or an award. It can only make problems visible.
- It cannot see what is never published, recorded or observed. Spending a contractor never records shows only as an unaccounted balance.
- It cannot prove wrongdoing. Flags point to where people with authority should look.

## Review requirements

Changes to these areas MUST have a second human reviewer: authentication, authorisation, keys and secrets, personal information, watchdog data, payroll data, the spend ledger, flag definitions, moderation rules, and anything that changes what the portal shows.

## Reporting vulnerabilities

See [SECURITY.md](../../SECURITY.md).
