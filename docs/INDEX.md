# Project Knowledge Index

## Read order for work

1. `docs/PROJECT.md` — project identity and boundaries
2. `docs/state/current.md` — current work and handoff
3. Relevant product, feature, architecture, and decision records
4. `openspec/specs/` — approved behavior
5. `openspec/changes/` — proposed or in-progress behavior

## Authority

1. Approved OpenSpec specifications and accepted ADRs
2. Current architecture documentation and verified implementation records
3. Active OpenSpec change artifacts
4. Raw material in `docs/inbox/`

If code and a record disagree, report the drift and ask for a decision when it
would change intent or behavior.

## Knowledge map

| Location | Purpose | Update trigger |
| --- | --- | --- |
| `docs/inbox/` | Immutable raw input | New unstructured input |
| `docs/product/` | Vision, requirements, vocabulary | Intent changes |
| `docs/features/` | Feature-level navigation | Feature becomes established |
| `openspec/specs/` | Canonical behavioral requirements | Approved behavior changes |
| `openspec/changes/` | Proposed and in-progress changes | Change lifecycle |
| `docs/architecture/` | Current technical design | Architecture changes |
| `docs/decisions/` | Decision history | Significant decision |
| `docs/operations/` | Running and releasing the system | Operational changes |
| `docs/state/` | Handoff, blockers, open questions | Meaningful work completes |
