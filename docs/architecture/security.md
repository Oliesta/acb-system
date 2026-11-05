# Security and Threat Model

Status: Proposed.

The main threat is not an outside hacker. It is **people inside the process working together**. A tamper-proof ledger only records what it is told. If an official, a contractor and an inspector agree to lie, a naive system records the lie permanently. The design must make collusion expensive, visible and risky.

## Threats and controls

| ID | Threat | Control | Rule |
|----|--------|---------|------|
| T1 | Official and supplier collude to claim work that was not done | Inspectors are assigned at random from an eligible pool, not chosen by the official or supplier | [MIL-004](../domains/milestones/rules.md) |
| T2 | Inspector is bribed or pressured | High-value milestones need two independent inspectors. Watchdog evidence can trigger re-inspection | [MIL-005](../domains/milestones/rules.md), [EVD-006](../domains/evidence/rules.md) |
| T3 | Fake or reused photos | Field app captures photos in-app only, with device time, GPS and a hash at capture. Duplicate image hashes are flagged | [EVD-002](../domains/evidence/rules.md), [EVD-003](../domains/evidence/rules.md) |
| T4 | GPS spoofing | GPS is one signal, not proof. Location MUST be checked against the site boundary and cross-checked with other evidence | [EVD-004](../domains/evidence/rules.md) |
| T5 | Same invoice paid twice, or across contracts | Invoice hash and invoice number per supplier are unique across the whole system | [PAY-004](../domains/payments/rules.md) |
| T6 | One official releases funds alone | N of M approvals from separate roles. The person who verified cannot approve | [PAY-002](../domains/payments/rules.md), [PAY-003](../domains/payments/rules.md) |
| T7 | Records changed after the fact | Ledger is append-only and anchored on-chain | [ADR-002](decision-records/ADR-002-public-chain-anchoring.md) |
| T8 | Scope inflated through variations | Variations are public events with reasons, and variations over a set share of contract value need extra approval | [TND-005](../domains/tenders/rules.md) |
| T9 | Payment to a deregistered or non-compliant supplier | CSD check before every release, not only at award | [PAY-005](../domains/payments/rules.md) |
| T10 | Watchdogs are identified and threatened | Watchdog identity is never public. Location data on watchdog submissions is delayed and coarsened on the portal | [EVD-007](../domains/evidence/rules.md), [DSC-004](../domains/disclosure/rules.md) |
| T11 | Personal information leaks through hashes | No hash of an individual's personal information goes on-chain. Only batch Merkle roots | [ADR-003](decision-records/ADR-003-personal-information-off-chain.md) |
| T12 | Anchoring key or admin key is stolen | Keys held in a hardware security module or managed key service. Admin actions need two people and are ledger events | To be written before Phase 1 |

## What the system cannot stop

Stated plainly so nobody oversells it:

- Corruption in the **award** itself (rigged specifications, bid collusion). The system makes award data public, which helps others detect it, but does not prevent it.
- Collusion between **every** person in the chain at once, including all random inspectors.
- Inflated pricing that was agreed at award. The portal makes prices comparable, but does not judge them.

## Review requirements

Changes to these areas MUST have a second human reviewer: authentication, authorisation, keys and secrets, personal information, the payment gate, anchoring, and anything that changes what the portal shows.

## Reporting vulnerabilities

See [SECURITY.md](../../SECURITY.md).
