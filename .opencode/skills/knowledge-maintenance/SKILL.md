---
name: Knowledge Maintenance
description: Maintain durable project knowledge while ingesting requirements, planning changes, implementing work, or handing off a session.
---

# Knowledge Maintenance

Use this skill whenever work can affect requirements, specifications, architecture,
decisions, project state, or raw project input.

1. Read `docs/INDEX.md`, `docs/state/current.md`, and records related to the work.
2. Treat `docs/inbox/` as immutable source material. Extract facts, assumptions,
   constraints, conflicts, and questions without rewriting the source.
3. Treat approved OpenSpec specs and ADRs as the highest documentary authority.
   When code disagrees, report the discrepancy rather than silently changing either.
4. Make material behavior changes in an OpenSpec change directory before coding.
   Keep proposal, design, tasks, and spec deltas internally consistent.
5. Maintain documents by event: behavior changes affect specs; technical structure
   affects architecture; major choices create ADRs; meaningful work updates state.
6. In the final report, distinguish completed verification, unverified claims,
   unresolved questions, and known documentation drift.
