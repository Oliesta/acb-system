# ADR-006: Phased rollout for an independent platform
Status: Proposed
Date: 2026-11-05
Owner: @Oliesta
Supersedes: [ADR-004](ADR-004-phased-rollout.md)

## Context
[ADR-005](ADR-005-independent-transparency-platform.md) makes the platform independent. The rollout no longer needs government partners, but community observations bring safety and legal risks that need preparation first.

## Decision
Build in phases. Each phase is useful on its own:

1. **Open data portal:** collect published tender and award data, link it per contract, archive snapshots, anchor on-chain.
2. **Flags:** publish risk indicators with a documented method and a right of reply.
3. **Community observations:** site reports from trained watchdogs in one pilot area, after the POPIA impact assessment and legal review.
4. **Scale:** more provinces and sources, voluntarily shared data, PAIA request tracking.

A phase MUST NOT start until the previous phase's exit criteria in the [Overview](../../context/overview.md) are met.

## Alternatives
- Observations first: rejected because watchdog safety and legal review need to be in place first, and the data portal gives observers something to check against.
- Flags in Phase 1: rejected because flag methods should be tested on real data before publication.

## Consequences
- Easier: Phase 1 needs no partners and shows results early.
- Harder: Phase 1 depends on the quality and availability of published data.

## Rules
- Exit criteria for each phase MUST be written in the [Overview](../../context/overview.md) before that phase starts.

## Review Trigger
Published source data turns out to be too poor for Phase 1.

## References
- Documentation: [Overview](../../context/overview.md)
- Tests or validation: not applicable
