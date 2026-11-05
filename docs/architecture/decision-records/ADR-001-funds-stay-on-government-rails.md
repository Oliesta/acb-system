# ADR-001: Funds stay on government payment rails
Status: Proposed
Date: 2026-11-05
Owner: @Oliesta

## Context
The original concept locked tender funds in smart contracts. That would mean holding public money as crypto assets or stablecoins. Public money must be kept in bank accounts and paid through systems controlled under the PFMA and MFMA. Public bodies cannot move budget into a smart contract, and no accounting officer would sign off on it. The idea would block adoption before any pilot.

What actually prevents corruption is not where money sits, but the rule that **no payment happens without verified evidence and independent approval**.

## Decision
The system acts as a payment release gate. It holds no funds. It sends a signed payment authorisation to the public body's existing financial system, which pays through normal bank rails and returns a payment reference.

## Alternatives
- Funds in smart contract escrow (stablecoin or tokenised Rand): rejected because it conflicts with public finance law, adds currency and custody risk, and needs central bank approval that does not exist for this use.
- Funds held by a third-party escrow bank: rejected for now because it adds cost and a new party to every contract. MAY be reconsidered for donor-funded pilots.
- Advisory only, no gate: rejected because a gate that can be ignored is a report, not a control.

## Consequences
- Easier: legal adoption, procurement of the system itself, integration with existing audit processes.
- Harder: the gate is only as strong as the public body's agreement to honour it. A payment made outside the gate is still possible, so it MUST be detectable.

## Rules
- PAY-001: The system MUST NOT hold, transfer or custody funds.
- PAY-007: Every payment recorded by the public body for a registered contract MUST match a gate authorisation. Unmatched payments MUST be flagged publicly.

## Review Trigger
A legal framework for tokenised public funds, or a pilot funder who requires on-chain escrow.

## References
- Documentation: [Architecture](../architecture.md), [Payments rules](../../domains/payments/rules.md)
- Tests or validation: none yet
