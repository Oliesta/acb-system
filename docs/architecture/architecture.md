# Architecture

Status: Proposed. Nothing here is built yet.

## Principles

1. **Independent.** The portal, observations and flags work from public sources and community observations alone. Only the spend ledger needs the contractor to take part. See [ADR-005](decision-records/ADR-005-independent-transparency-platform.md).
2. **Every Rand has a story.** Each awarded tender's spending is recorded line by line, with references that payees can check. See [ADR-007](decision-records/ADR-007-tender-spend-ledger.md).
3. **Observe and publish, never approve.** The system has no role in payments or government decisions.
4. **Every fact has a source.** Nothing appears on the portal without a source reference and snapshot.
5. **Tamper-evident.** Records are append-only and anchored on-chain. See [ADR-002](decision-records/ADR-002-public-chain-anchoring.md).
6. **Personal information never goes on-chain.** See [ADR-003](decision-records/ADR-003-personal-information-off-chain.md).
7. **Fair to the named.** Flags are explained and open to reply.

## Components

| Component | Responsibility | Domain rules |
|-----------|----------------|--------------|
| Spend ledger service | Hold budget lines, funds in and spend entries. Issue ACB references | [Spend ledger](../domains/spend/rules.md) |
| Contractor portal | Where contractors record spend entries, upload invoices and proof of payment | [Spend ledger](../domains/spend/rules.md) |
| Reference lookup | Public lookup of any ACB reference, and payee or worker confirmation | [Spend ledger](../domains/spend/rules.md) |
| Source collectors | Fetch published data from each source on a schedule | [Sources](../domains/sources/rules.md) |
| Snapshot archive | Store a copy and hash of every retrieved document | [Sources](../domains/sources/rules.md) |
| Contract record builder | Link source data into one record per contract | [Tenders](../domains/tenders/rules.md) |
| Field app | Mobile app for watchdogs. Captures photos in-app, works offline | [Evidence](../domains/evidence/rules.md) |
| Observation moderation | Review, redact and verify observations before publication | [Evidence](../domains/evidence/rules.md) |
| Flag engine | Run versioned flag definitions over contract records | [Flags](../domains/flags/rules.md) |
| Right of reply | Receive and publish replies from named suppliers and public bodies | [Flags](../domains/flags/rules.md) |
| Ledger | Append-only event log. Every change is an event | [ADR-002](decision-records/ADR-002-public-chain-anchoring.md) |
| Anchoring service | Batch ledger events into a Merkle tree and write the root on-chain | [ADR-002](decision-records/ADR-002-public-chain-anchoring.md) |
| Glass Pipe portal and API | Public website and open data downloads | [Disclosure](../domains/disclosure/rules.md) |

## How data flows

```text
Public sources (eTenders, public body sites, budgets, AG reports)
        |
        v
Source collectors --> Snapshot archive (copy + hash of each document)
        |
        v
Contract record builder: one record per contract, every fact sourced
        |            ^                              ^
        |            |                              |
        |   Contractor portal --> Spend ledger      |
        |   (spend entries, ACB references)         |
        |            ^                              |
        |            |                              |
        |   Suppliers and workers check             |
        |   their ACB reference                     |
        |                                           |
        |               Watchdogs --> Field app --> Moderation
        |                           (redacted, verified observations)
        v
Flag engine: published, versioned flag definitions
        |
        v
Right of reply: suppliers and public bodies respond
        |
        v
Glass Pipe portal and open data API
        
Every step is a ledger event, batched and anchored on a public chain.
```

## Where data lives

| Data | Store | Public? |
|------|-------|---------|
| Contract records, spend entries, flags, replies, ledger events | Off-chain database, append-only | Yes |
| Individual wage entries | Encrypted database | No. Totals per pay period are public |
| Invoices and proof of payment | Object storage, hashed | Redacted copies public |
| Source snapshots | Object storage | Yes, unless they contain personal information |
| Merkle roots of ledger batches | Public blockchain | Yes |
| Original observations | Encrypted object storage | No |
| Redacted, verified observations | Public object storage, may be mirrored to IPFS | Yes |
| Watchdog and moderator accounts | Encrypted database, access logged | No |

IPFS is optional for public copies. Content only stays on IPFS while someone pins it, so the system MUST keep its own copy of every public file.

## How the system can fail

Threats and controls are in [security.md](security.md). Failure modes to prepare for before Phase 1:

| Failure | How we know | First check |
|---------|-------------|-------------|
| A source changes its website layout | Records collected from that source drop by more than 50% against the 7-day average | Collector logs for that source |
| Anchoring stops | Time since last anchor exceeds 24 hours | Anchoring service logs and anchoring account balance |
| Contractor stops recording | No spend entries for 15 working days on an active project | Contractor portal activity for that contract |
| Reference lookup unavailable | Lookup error rate above 5% over 1 hour | Reference lookup service logs |
| Flag engine produces a burst of flags | Flags for one definition exceed 3 times the weekly average | Recent changes to that definition and its input data |
| Observation backlog | Observations awaiting moderation older than 7 days | Moderation queue size and moderator activity |

These become runbook entries once environments exist.
