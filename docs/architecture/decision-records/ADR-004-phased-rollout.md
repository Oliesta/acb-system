# ADR-004: Phased rollout, transparency first

> **Superseded.** Its phases included a payment gate, which [ADR-005](ADR-005-independent-transparency-platform.md) removes. See [ADR-006](ADR-006-phased-rollout-independent.md). Kept for its reasoning.

Status: Superseded by [ADR-006](ADR-006-phased-rollout-independent.md)
Date: 2026-11-05
Owner: @Oliesta

## Context
The full system needs agreements with public bodies, National Treasury (CSD) and financial system vendors. Those take a long time. A project that cannot show anything until all are in place will stall.

## Decision
Build in phases, where each phase is useful on its own and needs fewer partners than the next:

1. **Transparency:** public portal over already published tender and award data, with anchoring. No partner needed.
2. **Evidence:** milestone verification on one pilot project, preferably donor or NGO funded, so the funder can honour the gate without public finance integration.
3. **Payment gate:** one partner public body connects the gate to its financial system.
4. **Scale.**

A phase MUST NOT start until the previous phase's exit criteria are met.

## Alternatives
- Build everything, then pilot: rejected because there is nothing to show partners for a long time.
- Start with the payment gate: rejected because it needs the hardest partnership first.

## Consequences
- Easier: early, visible results. Partners can see a working portal before committing.
- Harder: Phase 1 depends on the quality of published data, which may be poor.

## Rules
- Exit criteria for each phase MUST be written in the [Overview](../../context/overview.md) before that phase starts.

## Review Trigger
A public body offers to partner on the payment gate before Phase 2 ends.

## References
- Documentation: [Overview](../../context/overview.md)
- Tests or validation: not applicable
