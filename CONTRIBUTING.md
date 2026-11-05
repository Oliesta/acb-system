# Contributing to the ACB System

Thank you for your interest in the ACB System. This guide explains how to contribute and what a contribution needs before it can be merged.

The project is at the concept stage. Most useful contributions right now are to the documentation: challenging decisions, testing rules against real procurement practice, and answering the open questions in the [Overview](docs/context/overview.md#open-questions).

## Contents

- [Ways to contribute](#ways-to-contribute)
- [How the project works: documentation first](#how-the-project-works-documentation-first)
- [Before you start](#before-you-start)
- [Making a change](#making-a-change)
- [Writing standards](#writing-standards)
- [Decision records](#decision-records)
- [Rule IDs](#rule-ids)
- [Pull requests](#pull-requests)
- [Review](#review)
- [Reporting security issues](#reporting-security-issues)
- [Conduct](#conduct)
- [Licence](#licence)

## Ways to contribute

| Contributor | Where to start |
|-------------|----------------|
| Developers and architects | Review the [Architecture](docs/architecture/architecture.md) and the [decision records](docs/architecture/decision-records/). |
| Security reviewers | Test the [threat model](docs/architecture/security.md) for gaps, especially ways to collude around a rule. |
| Construction, procurement and finance professionals | Check the [Spend ledger rules](docs/domains/spend/rules.md) and [Flags rules](docs/domains/flags/rules.md) against how projects are actually run and paid. |
| Legal professionals | Help with open question Q5 (defamation, POPIA and PAIA) in the [Overview](docs/context/overview.md#open-questions). |
| Data specialists and journalists | Identify and assess public data sources for the [Sources rules](docs/domains/sources/rules.md). |
| Community organisations | Help shape the watchdog programme in the [Evidence rules](docs/domains/evidence/rules.md). |

If you are unsure where your contribution fits, open an issue and describe what you would like to do.

## How the project works: documentation first

The documentation in [docs](docs/README.md) is the source of truth. Code is built from it, not the other way round.

- If code and documentation disagree, the documentation is correct until a maintainer decides otherwise. Report the disagreement in an issue. Do not silently change either one.
- Every change, including a one-line fix, starts with the documentation.
- A human maintainer approves every change and owns every decision.

## Before you start

1. Read the [Overview](docs/context/overview.md) and the [Glossary](docs/context/glossary.md). Use glossary terms exactly.
2. Read the domain rules and decision records that relate to your change.
3. Search open issues and pull requests to avoid duplicate work.
4. For anything larger than a correction, open an issue first so the approach can be agreed before you invest time.

## Making a change

Every change follows these five steps, in order:

1. **Define.** Add or update the rule, requirement or acceptance criteria in the relevant document.
2. **Decide.** If the change is a real choice between alternatives, or affects architecture, security, privacy, cost or independence, write a new decision record or name the existing one that still holds. Check its Review Trigger before contradicting it.
3. **Build.** Implement the change following the documentation.
4. **Verify.** Add or update tests. Name tests after the Rule IDs they cover, for example `test_SPD_009_reference_required_on_invoice`.
5. **Reconcile.** Fix any remaining gap between documentation and code, update every affected link, and add an entry to the [documentation changelog](docs/CHANGELOG.md).

A change that has no effect on the documentation MUST say so in the pull request with the line `No doc impact, because <reason>`.

### Branches and commits

- Fork the repository and create a branch from `main`, named after the change, for example `docs/spend-ledger-vat` or `fix/flag-f10-threshold`.
- Keep each pull request to one logical change.
- Write commit messages in the imperative, with a short summary line, for example `Add VAT handling to spend entries`.

## Writing standards

- **Rule keywords.** Use MUST, MUST NOT, SHOULD, SHOULD NOT and MAY in capitals, with their usual meaning.
- **One fact, one place.** State each fact once and link to it elsewhere.
- **Be specific.** Replace words such as "fast", "secure" or "as needed" with numbers or conditions.
- **Give examples.** Show a valid and an invalid case for rules where the boundary is not obvious.
- **Cover edge cases.** Consider empty, duplicate, concurrent, expired and unauthorised cases.
- **Plain language.** Use short sentences and South African English spelling.
- **No em dashes.** Use a full stop, comma, colon or brackets instead.
- **Links.** Use repository-relative Markdown links with descriptive text. Never use "click here", local file paths or line numbers. Check that every link target exists.
- **Archiving.** Superseded documents move to [docs/archive](docs/archive/), marked as superseded with a link to their replacement. Reasoning is never deleted.

## Decision records

Decision records (ADRs) live in [docs/architecture/decision-records](docs/architecture/decision-records/).

- Copy the structure of an existing ADR: Status, Date, Owner, Context, Decision, Alternatives, Consequences, Rules, Review Trigger and References.
- Use the next free number. ADR numbers are never reused or renumbered.
- Keep each ADR to one decision.
- New ADRs start as **Proposed**. Only a maintainer can mark an ADR as **Accepted**.
- An accepted ADR is not edited in substance. A changed decision needs a new ADR that supersedes it.
- Add the new ADR to the table in the [documentation index](docs/README.md).

## Rule IDs

Every rule has an ID made of a domain prefix and a number, for example `SPD-009`.

| Prefix | Domain |
|--------|--------|
| `SPD` | [Spend ledger](docs/domains/spend/rules.md) |
| `SRC` | [Sources](docs/domains/sources/rules.md) |
| `TND` | [Tenders](docs/domains/tenders/rules.md) |
| `EVD` | [Evidence](docs/domains/evidence/rules.md) |
| `FLG` | [Flags](docs/domains/flags/rules.md) |
| `DSC` | [Disclosure](docs/domains/disclosure/rules.md) |
| `IND`, `LED`, `PRV` | Defined in decision records ADR-005, ADR-002 and ADR-003 |

- Use the next free number in the domain. Retired IDs, including the archived `MIL` and `PAY` rules, MUST NOT be reused.
- Update the Rule Ownership table in the domain's `rules.md` when you add a rule.

## Pull requests

Pull requests use the [pull request template](.github/pull_request_template.md). A pull request is ready for review when:

- [ ] The relevant documentation is updated, or `No doc impact, because <reason>` is stated.
- [ ] Affected Rule IDs are listed.
- [ ] The relevant decision record is named, or a new one is included.
- [ ] Tests or validation cover the affected rules, where code is involved.
- [ ] Every link added or changed has been checked.
- [ ] The [documentation changelog](docs/CHANGELOG.md) has an entry.
- [ ] No personal information, credentials or real people's data appear anywhere in the change.

## Review

Every pull request needs approval from a maintainer.

Changes that touch the following areas MUST also be approved by a second reviewer:

- authentication, authorisation, keys or secrets
- personal information, payroll data or watchdog data
- the spend ledger, ACB references or anchoring
- flag definitions or moderation rules
- anything that changes what the public portal shows

Reviewers check that the change does what the updated documentation says and nothing more, that boundaries between domains are respected, and that there are no unrequested dependencies or files.

## Reporting security issues

Do not open a public issue for a vulnerability. Follow the process in [SECURITY.md](SECURITY.md).

Design weaknesses, such as a way to collude around a rule, may be raised as public issues because the design is already public. Please reference the threat ID or Rule ID concerned.

## Conduct

This project deals with corruption, which involves real people and organisations. Contributors are expected to:

- be respectful and constructive in all discussions
- never name or accuse individuals in issues, pull requests, commits or test data
- use invented names and figures in examples and tests
- keep discussion focused on the system, not on political parties or personalities

Maintainers may remove content or contributors that do not meet these expectations.

## Licence

By contributing, you agree that your contributions are licensed under the project's [MIT Licence](LICENSE).
