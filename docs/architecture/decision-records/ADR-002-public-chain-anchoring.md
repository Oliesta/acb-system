# ADR-002: Anchor batched hashes to a public chain
Status: Proposed
Date: 2026-11-05
Owner: @Oliesta

## Context
The ledger must be tamper-evident to people who do not trust the operator, including future governments. Storing every record on a blockchain is costly, slow and risky for privacy. A database alone can be quietly edited by whoever runs it.

## Decision
Ledger events are stored in an append-only off-chain database. At a fixed interval, events are batched into a Merkle tree and only the root hash is written to a public blockchain. Anyone can download the events and check them against the on-chain root.

## Alternatives
- Every event on-chain: rejected because of cost, throughput and the risk of leaking data.
- Permissioned chain run by government: rejected for now because the operators are the parties being checked, so it gives little independent assurance.
- No chain, signed database only: rejected because signatures prove who wrote a record, not that history was not rewritten.

## Consequences
- Easier: low cost per record, public chain choice can change without data migration, no personal information on-chain.
- Harder: records are only proven at anchor time, so there is a window between event and anchor. Anchoring itself becomes a service that must be monitored.

## Rules
- LED-001: Ledger events MUST be append-only. Corrections are new events that reference the original.
- LED-002: A batch MUST be anchored at least every 24 hours, and within 1 hour of a new flag or a published community observation.
- LED-003: The portal MUST let anyone download a batch and verify it against its on-chain root.

## Review Trigger
Anchoring cost exceeds an agreed monthly budget, or the chosen chain changes its security model. The chain choice itself is open question Q3 in the [Overview](../../context/overview.md).

## References
- Documentation: [Architecture](../architecture.md), [Security](../security.md)
- Tests or validation: none yet
