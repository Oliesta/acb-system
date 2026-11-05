# ADR-005: Independent transparency platform, no role in approving funds
Status: Proposed
Date: 2026-11-05
Owner: @Oliesta
Supersedes: [ADR-001](ADR-001-funds-stay-on-government-rails.md)

## Context
The earlier design made the ACB System a payment release gate inside government processes. The maintainer clarified that this was never the intent. The ACB System exists so the **public** can see how public money is spent and spot problems. It must work **independently** of the public bodies it watches.

A gate also has real drawbacks: it needs every public body to agree to it, it makes the system part of the process it should be watching, and the operator would carry legal responsibility for payment decisions.

## Decision
The ACB System is an independent, public transparency platform. It collects public procurement data, a per-tender record of how the awarded funds are spent, and community observations, links them per contract, highlights risk indicators (flags), and publishes everything in a tamper-evident way. It **never** approves, blocks, authorises or holds payments, and it does not need any public body's cooperation to work.

## Alternatives
- Payment release gate (ADR-001): rejected because it is not the project's purpose and depends on government cooperation.
- Advisory tool used inside public bodies: rejected because it would be controlled by the bodies being watched.
- Pure open data mirror with no flags or observations: rejected because raw data alone is hard for the public to use.

## Consequences
- Easier: no partnership is needed to start, the platform stays independent, and the operator has no payment liability.
- Harder: the platform can detect and expose, but not prevent. Impact depends on citizens, journalists and oversight bodies acting on what it shows. Publishing flags about named suppliers and public bodies creates defamation risk, so flags must be factual, explained and open to reply (see [Flags rules](../../domains/flags/rules.md)).

## Rules
- IND-001: The system MUST NOT approve, block, authorise, hold or move any payment.
- IND-002: The open data portal, community observations and flags MUST work using only lawful public sources and community observations, without any public body's cooperation. The spend ledger ([ADR-007](ADR-007-tender-spend-ledger.md)) needs the awarded contractor to record entries. That participation MAY be a contract condition set by the public body, or voluntary. A contractor that does not take part MUST be shown as not participating, not hidden.
- IND-003: Data a public body chooses to share MAY be included, and MUST be labelled with its source.
- IND-004: The project MUST NOT accept funding or terms that give any public body or supplier control over what is published.

## Review Trigger
A public body asks to use the platform as an internal control, or the legal review (open question Q5) finds the publishing model unsafe.

## References
- Documentation: [Overview](../../context/overview.md), [Architecture](../architecture.md), [Sources rules](../../domains/sources/rules.md), [Flags rules](../../domains/flags/rules.md)
- Tests or validation: none yet
