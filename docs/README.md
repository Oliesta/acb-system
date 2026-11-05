# ACB System Documentation

These docs are the source of truth for the ACB System. Code is derived from them. If code and docs disagree, the docs win until a human decides otherwise.

## Start here

1. [Overview](context/overview.md): the problem, who it is for, what it does and does not do, and the phased plan.
2. [Village stadium example](context/example-stadium.md): the original ACB idea, worked through for a R10,000,000 tender.
3. [Glossary](context/glossary.md): the exact meaning of every project term.
4. [Architecture](architecture/architecture.md): components, data flow and trust model.
5. [Security and threat model](architecture/security.md): how the system can be attacked, including by insiders.

## Decisions

Architecture Decision Records (ADRs) live in [decision-records](architecture/decision-records/).

| ADR | Title | Status |
|-----|-------|--------|
| [ADR-001](architecture/decision-records/ADR-001-funds-stay-on-government-rails.md) | Funds stay on government payment rails | Superseded by ADR-005 |
| [ADR-002](architecture/decision-records/ADR-002-public-chain-anchoring.md) | Anchor batched hashes to a public chain | Proposed |
| [ADR-003](architecture/decision-records/ADR-003-personal-information-off-chain.md) | Personal information stays off-chain | Proposed |
| [ADR-004](architecture/decision-records/ADR-004-phased-rollout.md) | Phased rollout, transparency first | Superseded by ADR-006 |
| [ADR-005](architecture/decision-records/ADR-005-independent-transparency-platform.md) | Independent transparency platform, no role in approving funds | Proposed |
| [ADR-006](architecture/decision-records/ADR-006-phased-rollout-independent.md) | Phased rollout for an independent platform | Proposed |
| [ADR-007](architecture/decision-records/ADR-007-tender-spend-ledger.md) | Tender spend ledger with ACB references | Proposed |

## Domain rules

Each domain has a `rules.md` with Rule IDs, edge cases and acceptance criteria.

| Domain | Prefix | Responsibility |
|--------|--------|----------------|
| [Spend ledger](domains/spend/rules.md) | `SPD` | Budget lines, spend entries and ACB references per tender |
| [Sources](domains/sources/rules.md) | `SRC` | Collecting public data, snapshots and provenance |
| [Tenders](domains/tenders/rules.md) | `TND` | One linked record per tender and contract |
| [Evidence](domains/evidence/rules.md) | `EVD` | Community observations and the watchdog programme |
| [Flags](domains/flags/rules.md) | `FLG` | Risk indicators and the right of reply |
| [Disclosure](domains/disclosure/rules.md) | `DSC` | What the public portal shows, and what it never shows |

Retired rule sets (`MIL`, `PAY`) are in the [archive](archive/).

## How to change anything

Every change follows five steps, even a one-line fix:

1. **Define:** update the rule or acceptance criteria in the relevant doc.
2. **Decide:** if it is a real choice between alternatives, write or cite an ADR.
3. **Generate:** implement it.
4. **Verify:** add tests named after the Rule IDs.
5. **Reconcile:** fix gaps, update links and the [CHANGELOG](CHANGELOG.md).

Every pull request MUST include a doc update or the line `No doc impact, because <reason>`.

## Writing rules

- Rules use MUST, MUST NOT, SHOULD and MAY in capitals.
- One fact lives in one place. Link to it instead of repeating it.
- Use numbers and conditions, not words like "fast" or "secure".
- No em dashes.
- Superseded docs move to [archive](archive/) with a link to their replacement. Reasoning is never deleted.
