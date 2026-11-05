# Architecture

Status: Proposed. Nothing here is built yet.

## Principles

1. **Independent.** Every core feature works from public sources and community observations alone. See [ADR-005](decision-records/ADR-005-independent-transparency-platform.md).
2. **Observe and publish, never approve.** The system has no role in payments or government decisions.
3. **Every fact has a source.** Nothing appears on the portal without a source reference and snapshot.
4. **Tamper-evident.** Records are append-only and anchored on-chain. See [ADR-002](decision-records/ADR-002-public-chain-anchoring.md).
5. **Personal information never goes on-chain.** See [ADR-003](decision-records/ADR-003-personal-information-off-chain.md).
6. **Fair to the named.** Flags are explained and open to reply.

## Components

| Component | Responsibility | Domain rules |
|-----------|----------------|--------------|
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
        |                                   ^
        |                                   |
        |               Watchdogs --> Field app --> Moderation
        |                                   (redacted, verified observations)
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
| Contract records, flags, replies, ledger events | Off-chain database, append-only | Yes |
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
| Anchoring stops | Time since last anchor exceeds 24 hours | Anchoring service logs and wallet balance |
| Flag engine produces a burst of flags | Flags for one definition exceed 3 times the weekly average | Recent changes to that definition and its input data |
| Observation backlog | Observations awaiting moderation older than 7 days | Moderation queue size and moderator activity |

These become runbook entries once environments exist.
