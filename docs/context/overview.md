# Overview

## Problem

Procurement corruption in South Africa is mostly found after the money is gone, through Special Investigating Unit (SIU) investigations and Auditor-General reports that arrive months or years later.

One reason is that procurement information is hard for the public to use:

- **Scattered:** tender notices, awards, budgets and audit findings sit on different websites, in different formats.
- **Unlinked:** nothing connects a tender notice to its award, its variations, its spending and what was actually built.
- **Invisible spending:** once a tender is awarded, the public cannot see how the contractor spends the money. Inflated invoices, fake suppliers and ghost workers stay hidden until an audit.
- **Mutable:** documents can be changed or removed after publication, and nobody can prove it.
- **Unchecked on the ground:** nobody outside the process compares what was paid for with what exists on site.

## What the ACB System is

The ACB System is an **independent, open-source transparency platform** for public procurement. It:

1. **Tracks spending** with a **spend ledger** per tender: the award budget split into line items, with every purchase and payroll run recorded against a line. Each entry gets a unique **ACB reference** that goes on the invoice, so anyone holding the invoice can check it. See [ADR-007](../architecture/decision-records/ADR-007-tender-spend-ledger.md).
2. **Collects** published procurement data from public sources and keeps snapshots of it.
3. **Links** it into one record per contract, from notice to award to completion.
4. **Adds** verified community observations of what is actually happening on site.
5. **Highlights** risk indicators (flags) using published, explained methods, with a right of reply.
6. **Publishes** everything on a public portal, the **Glass Pipe**, and anchors it to a public blockchain so nobody can quietly rewrite history.

The [village stadium example](example-stadium.md) shows how this works for a R10,000,000 tender.

The portal, observations and flags work without any public body's cooperation. The spend ledger needs the contractor to record entries, either as a contract condition or voluntarily. See [ADR-005](../architecture/decision-records/ADR-005-independent-transparency-platform.md).

## What the ACB System is not

- It does **not** approve, block, authorise or hold payments. It has no role in government processes.
- It is **not** a wallet. The spend ledger mirrors spending in Rand. Its entries are records with no value.
- It is **not** an investigator or a court. Flags are indicators for review, never findings of wrongdoing.
- It is **not** a cryptocurrency or token project.
- It does **not** store personal information on a blockchain. See [ADR-003](../architecture/decision-records/ADR-003-personal-information-off-chain.md).

## Who it is for

| Stakeholder | What they get |
|-------------|---------------|
| Citizens and communities | Plain-language view of what was bought in their area, from whom, and whether it was delivered |
| Journalists and researchers | Linked, downloadable data with sources and snapshots |
| Civil society organisations | Evidence to support campaigns and PAIA requests |
| Oversight bodies (AGSA, SIU, Public Protector, legislatures) | Leads worth investigating, with a tamper-evident trail |
| Contractors | A public record of clean spending that wins trust and future work, and a right of reply to any flag. They record every spend in the ledger |
| Subcontractors, suppliers and workers | A way to check that their invoice or wage was recorded correctly, using the ACB reference |
| Public bodies | A free, independent check they can point to, and a channel to correct or add data |

## How impact happens

The platform does not stop corruption itself. It makes problems **visible early**, while there is still time for people with authority to act. Impact depends on others using what it shows, so the portal MUST make it easy to share a contract record, download evidence and report concerns to the right oversight body.

## Phased plan

Details and reasoning are in [ADR-006](../architecture/decision-records/ADR-006-phased-rollout-independent.md).

| Phase | Scope | Exit criteria (proposed) |
|-------|-------|--------------------------|
| 0. Concept | Docs, ADRs, threat model | ADRs accepted, legal review started |
| 1. Prototype | Spend ledger, ACB references, portal and anchoring, shown with the stadium example. Published tender data for one province | Stadium example runs end to end; legal review and POPIA impact assessment started |
| 2. Pilot project | One real project: contractor records every spend, watchdogs on site, ledger flags with right of reply | Legal review and POPIA impact assessment complete; contractor signed up; 20 watchdogs trained |
| 3. Public data flags | Flags F01 to F09 over a province's published tender data | Each flag definition reviewed by an independent expert |
| 4. Scale | More projects and provinces, optional bank feeds, PAIA request tracking | Set before Phase 4 starts |

## Success measures

Proposed targets, to be confirmed before Phase 1 ends.

| Measure | Proposed target |
|---------|-----------------|
| Pilot spend entries recorded within 5 working days | 95% or more |
| Pilot funds in that are accounted for by spend entries | 95% or more at all times |
| Pilot spend entries over R100,000 confirmed by payee | 80% or more |
| Time from source publication to portal | 24 hours or less |
| Facts on the portal with a source and snapshot | 100% |
| Flags withdrawn as wrongly calculated | Under 2% |
| Replies published within 5 working days | 100% of valid replies |
| Personal information found on-chain or on the portal | 0 |
| Contract records shared or cited by journalists, CSOs or oversight bodies | Tracked from Phase 1 |

## Legal context

- Protection of Personal Information Act, 2013 (POPIA)
- Promotion of Access to Information Act, 2000 (PAIA), as a way to request records that are not published
- Protected Disclosures Act, 2000, for people who report wrongdoing
- Defamation law, because flags name companies and public bodies
- PFMA, MFMA, PPPFA and the Public Procurement Act, 2024, for what public bodies are required to publish

## Open questions

Owned by the maintainer. Each MUST be answered before the phase named.

| # | Question | Needed before |
|---|----------|---------------|
| Q1 | What is a sourced, citable figure for annual procurement losses? | Any public pitch |
| Q2 | Does the eTender Publication Portal provide machine-readable award data (for example OCDS)? | Phase 1 |
| Q3 | Which public chain do we anchor to? See [ADR-002](../architecture/decision-records/ADR-002-public-chain-anchoring.md). | Phase 1 |
| Q4 | Which province for Phase 1, and which pilot project, contractor and community partner for Phase 2? | Phase 1 and 2 |
| Q8 | Will the pilot contractor take part voluntarily, or will the funder or municipality make it a contract condition? | Phase 2 |
| Q5 | Legal review: defamation risk of flags, POPIA basis for processing supplier and payroll data, and whether the journalism exclusion in POPIA applies. | Phase 2 |
| Q6 | Which legal entity (for example a non-profit company or trust) will operate the platform, hold data and receive grants? | Phase 1 |
| Q7 | Funding policy: from whom will the project accept funding, given [IND-004](../architecture/decision-records/ADR-005-independent-transparency-platform.md)? | Phase 1 |
