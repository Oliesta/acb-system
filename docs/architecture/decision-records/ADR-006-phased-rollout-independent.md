# ADR-006: Phased rollout for an independent platform
Status: Proposed
Date: 2026-11-05
Owner: @Oliesta
Supersedes: [ADR-004](ADR-004-phased-rollout.md)

## Context
[ADR-005](ADR-005-independent-transparency-platform.md) makes the platform independent, and [ADR-007](ADR-007-tender-spend-ledger.md) makes the spend ledger its core. The ledger needs a participating contractor. Community observations bring safety and legal risks that need preparation first.

## Decision
Build in phases. Each phase is useful on its own:

1. **Prototype:** the spend ledger with ACB references, the public portal, and anchoring, demonstrated with the [stadium example](../../context/example-stadium.md). Published tender and award data for one province is loaded alongside.
2. **Pilot project:** one real project where the contractor records every spend, with trained watchdogs on site and ledger flags with a right of reply. Preferably donor or NGO funded, or a municipality that makes participation a contract condition. Starts only after the POPIA impact assessment and legal review.
3. **Public data flags:** flags over published tender data for a whole province.
4. **Scale:** more projects and provinces, payee confirmation at scale, optional read-only bank feeds, PAIA request tracking.

A phase MUST NOT start until the previous phase's exit criteria in the [Overview](../../context/overview.md) are met.

## Alternatives
- Public data portal only, ledger later: rejected because the spend ledger is the core idea and needs early testing with real contractors.
- Pilot without a prototype: rejected because partners need to see a working ledger before joining.

## Consequences
- Easier: Phase 1 needs no partners and shows the full idea early.
- Harder: Phase 2 needs one contractor willing to record every spend.

## Rules
- Exit criteria for each phase MUST be written in the [Overview](../../context/overview.md) before that phase starts.

## Review Trigger
No pilot contractor can be found within 6 months of Phase 1 ending.

## References
- Documentation: [Overview](../../context/overview.md)
- Tests or validation: not applicable
