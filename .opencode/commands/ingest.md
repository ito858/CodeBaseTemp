---
description: Preserve and structure raw requirements into a proposed change
---

Use the knowledge-maintenance skill. Ingest the raw material at `$1`.

If it is outside `docs/inbox/`, first preserve an unchanged copy under
`docs/inbox/YYYY-MM-DD-<topic>.md` and record its source. Read the knowledge index,
state, relevant specs, ADRs, and implementation before interpreting the input.
Extract atomic functional and non-functional requirements, constraints, assumptions,
conflicts, and unanswered questions. Do not invent answers. Create or update a
lowercase-kebab-case `openspec/changes/<change-name>/` proposal with spec deltas,
design notes, and tasks as appropriate. Clearly mark it as proposed and ask for
approval before treating material new behavior as authoritative.
