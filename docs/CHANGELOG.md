# Documentation Changelog

## 2026-11-05 (later)

- Clarified the core purpose: the ACB System is an independent public transparency platform. It does not approve, block or hold payments. See [ADR-005](architecture/decision-records/ADR-005-independent-transparency-platform.md).
- Superseded ADR-001 by ADR-005, and ADR-004 by ADR-006.
- Archived the payments (`PAY`) and milestones (`MIL`) rules. Their IDs are retired.
- Added Sources (`SRC`) and Flags (`FLG`) rules. Rewrote Tenders, Evidence and Disclosure rules.
- Rewrote the overview, glossary, architecture and threat model around independence, provenance, right of reply and watchdog safety.
- Changed LED-002 in ADR-002 to anchor after new flags and observations instead of payment authorisations.

## 2026-11-05

- Created the documentation structure.
- Refined the concept: the system is an evidence and approval layer over existing government payment rails, not a custodian of public funds. See [ADR-001](architecture/decision-records/ADR-001-funds-stay-on-government-rails.md).
- Added ADR-001 to ADR-004 as Proposed.
- Added domain rules for tenders, milestones, evidence, payments and disclosure.
- Removed all references to REVOICE AI (Pty) Ltd. The project has no lead company.
