# ACB System Documentation

These docs are the source of truth for the ACB System. Code is derived from them. If code and docs disagree, the docs win until a human decides otherwise.

## Start here

1. [Overview](context/overview.md): the problem, who it is for, what it does and does not do, and the phased plan.
2. [Glossary](context/glossary.md): the exact meaning of every project term.
3. [Architecture](architecture/architecture.md): components, data flow and trust model.
4. [Security and threat model](architecture/security.md): how the system can be attacked, including by insiders.

## Decisions

Architecture Decision Records (ADRs) live in [decision-records](architecture/decision-records/).

| ADR | Title | Status |
|-----|-------|--------|
| [ADR-001](architecture/decision-records/ADR-001-funds-stay-on-government-rails.md) | Funds stay on government payment rails | Proposed |
| [ADR-002](architecture/decision-records/ADR-002-public-chain-anchoring.md) | Anchor batched hashes to a public chain | Proposed |
| [ADR-003](architecture/decision-records/ADR-003-personal-information-off-chain.md) | Personal information stays off-chain | Proposed |
| [ADR-004](architecture/decision-records/ADR-004-phased-rollout.md) | Phased rollout, transparency first | Proposed |

## Domain rules

Each domain has a `rules.md` with Rule IDs, edge cases and acceptance criteria.

| Domain | Prefix | Responsibility |
|--------|--------|----------------|
| [Tenders](domains/tenders/rules.md) | `TND` | Tender, award and contract records |
| [Milestones](domains/milestones/rules.md) | `MIL` | Milestone definitions, claims and verification decisions |
| [Evidence](domains/evidence/rules.md) | `EVD` | Inspection evidence, invoices and the watchdog programme |
| [Payments](domains/payments/rules.md) | `PAY` | The payment release gate and approvals |
| [Disclosure](domains/disclosure/rules.md) | `DSC` | What the public portal shows, and what it never shows |

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
