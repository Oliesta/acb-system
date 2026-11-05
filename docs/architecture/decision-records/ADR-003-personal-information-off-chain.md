# ADR-003: Personal information stays off-chain
Status: Proposed
Date: 2026-11-05
Owner: @Oliesta

## Context
POPIA gives people the right to have their personal information corrected or deleted. Data on a blockchain cannot be deleted. Hashing does not fix this: an SA ID number has a small enough format that its hash can be reversed by trying every value. A hash of personal information is still personal information.

## Decision
No personal information, and no hash or encoding of an individual's personal information, is written on-chain. Only batch Merkle roots go on-chain (see [ADR-002](ADR-002-public-chain-anchoring.md)). Personal information is stored encrypted off-chain and referenced by internal IDs.

## Alternatives
- Hashed IDs on-chain: rejected because they are reversible for structured data such as ID and phone numbers.
- Salted hashes on-chain: rejected because the salt must be stored somewhere, so the data is only pseudonymised, and deletion is still impossible.

## Consequences
- Easier: POPIA deletion and correction requests can be honoured.
- Harder: some public checks need the operator's off-chain data, so data availability becomes important.

## Rules
- PRV-001: Personal information MUST NOT be written to any blockchain, in plain, hashed or encoded form.
- PRV-002: Personal information MUST be encrypted at rest, and every read MUST be logged with who read it and why.
- PRV-003: Leaf records in a Merkle batch that could contain personal information MUST include a random value per record, stored off-chain, so the root reveals nothing.
- PRV-004: A full POPIA impact assessment MUST be completed before Phase 2.

## Review Trigger
A change to POPIA or regulator guidance on blockchain data.

## References
- Documentation: [Disclosure rules](../../domains/disclosure/rules.md), [Security](../security.md)
- Tests or validation: none yet
