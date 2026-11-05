# Architecture

Status: Proposed. Nothing here is built yet.

## Principles

1. **Money stays where it is.** The system authorises payments. It never holds funds. See [ADR-001](decision-records/ADR-001-funds-stay-on-government-rails.md).
2. **Evidence before payment.** No milestone payment is authorised without accepted evidence. See [Payments rules](../domains/payments/rules.md).
3. **No single person decides.** Verification and approval each need people in separate roles.
4. **Tamper-evident, not just tamper-resistant.** Records may be stored in an ordinary database, but any change after the fact is detectable through on-chain anchors. See [ADR-002](decision-records/ADR-002-public-chain-anchoring.md).
5. **Personal information never goes on-chain.** See [ADR-003](decision-records/ADR-003-personal-information-off-chain.md).

## Components

| Component | Responsibility | Domain rules |
|-----------|----------------|--------------|
| Contract registry | Stores contracts, suppliers (by CSD number) and milestones | [Tenders](../domains/tenders/rules.md), [Milestones](../domains/milestones/rules.md) |
| Evidence service | Receives photos, reports and invoices, stores originals encrypted, produces redacted public copies | [Evidence](../domains/evidence/rules.md) |
| Field app | Mobile app for inspectors and watchdogs. Works offline and syncs later | [Evidence](../domains/evidence/rules.md) |
| Verification service | Assigns inspectors, records verification decisions | [Milestones](../domains/milestones/rules.md) |
| Payment release gate | Checks gate rules, collects approvals, sends a signed authorisation to the public body's financial system | [Payments](../domains/payments/rules.md) |
| Supplier checks | Checks CSD status (registration, tax compliance, bank verification) at award and before each release | [Payments](../domains/payments/rules.md) |
| Ledger | Append-only event log. Every state change is an event | All |
| Anchoring service | Batches ledger events into a Merkle tree and writes the root to a public chain | [ADR-002](decision-records/ADR-002-public-chain-anchoring.md) |
| Glass Pipe portal | Public read-only website and open data API | [Disclosure](../domains/disclosure/rules.md) |

## Flow of one milestone payment

```text
Supplier submits claim + invoice
        |
        v
Evidence service stores original (encrypted) and redacted copy
        |
        v
Verification service assigns inspector(s) at random from an eligible pool
        |
        v
Inspector(s) submit on-site evidence from the field app
        |
        v
Verification decision recorded: Accepted / Rejected / Needs more evidence
        |
        v (Accepted)
Payment gate: supplier CSD check, budget check, duplicate invoice check
        |
        v
Approvers in separate roles sign the release (N of M)
        |
        v
Signed authorisation sent to the public body's financial system
        |
        v
Public body pays through its normal bank rails, sends back the payment reference
        |
        v
Every step above is a ledger event, batched and anchored on-chain,
and shown on the Glass Pipe portal (without personal information)
```

## Where data lives

| Data | Store | Public? |
|------|-------|---------|
| Ledger events (no personal information) | Off-chain database, append-only | Yes, through the portal and API |
| Merkle roots of ledger batches | Public blockchain | Yes |
| Original invoices and evidence | Encrypted object storage | No. Oversight bodies by agreement |
| Redacted invoices and evidence | Public object storage, may be mirrored to IPFS | Yes |
| Personal information (inspectors, watchdogs, supplier contacts, bank details) | Encrypted database, access logged | No |

IPFS is optional for public copies. It is not a storage guarantee on its own: content is only kept while someone pins it. The system MUST keep its own copy of every public file.

## How the system can fail

Full threat model: [security.md](security.md). Key failure modes to prepare for before Phase 2:

| Failure | How we know | First check |
|---------|-------------|-------------|
| Anchoring stops (chain fees, key problem, network) | Time since last anchor exceeds 24 hours | Anchoring service logs and wallet balance |
| Field app evidence does not sync | Claims stuck in "awaiting evidence" past their deadline | Device sync queue and evidence service logs |
| Financial system rejects an authorisation | No payment reference returned within 5 working days | Integration logs for that authorisation ID |
| CSD check unavailable | Supplier check returns "unknown" | CSD integration status. Releases MUST wait, not pass |

These become runbook entries once environments exist.
