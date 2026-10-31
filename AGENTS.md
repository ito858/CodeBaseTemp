# Project Knowledge Protocol

## Principle

Prompting is temporary; structure is permanent. The repository, not chat history,
is the project memory.

## Authority and conflict handling

When records disagree, use this order: approved `openspec/specs/` and ADRs;
current architecture records and verified implementation; active OpenSpec changes;
raw inbox material. Code is evidence of implemented behavior, not automatic proof
that a conflicting specification is correct. Flag drift rather than silently
choosing a winner.

## Before changing code or durable documentation

1. Read `docs/INDEX.md`, `docs/state/current.md`, and the relevant records.
2. Check applicable OpenSpec specs, active changes, and ADRs.
3. Identify contradictions, assumptions, and unanswered questions.
4. For material behavior changes, create or update an OpenSpec change before
   implementation. Ask for approval where intent is ambiguous.

## Working with raw requirements

- Preserve supplied material unchanged in `docs/inbox/`.
- Extract atomic, testable requirements; distinguish facts from assumptions.
- Put unresolved items in `docs/state/open-questions.md`.
- Do not silently replace an approved requirement or decision.

## Credentials during database or VPS exploration

- Never read, print, copy, search, or disclose credential files such as `.env`
  or `.env.*`; `.env.exam**` files are safe examples only.
- When database access or SSH/VPS work needs credentials from an environment
  file, write or run a narrowly scoped command or script that loads the required
  variables without printing them. Prefer documented variable names and pass
  credentials through the process environment, not command-line arguments.
- Disable shell tracing for credential-loading commands, avoid diagnostic output
  that could reveal secrets, and do not persist generated credential-bearing
  scripts or logs in the repository.
- Report the command's non-sensitive outcome and any connection error, never
  the secret values or their file contents.

## During and after implementation

- Follow approved specs and keep change tasks accurate.
- Record significant technical choices as ADRs.
- Update only affected canonical records: behavioral changes update OpenSpec
  specs; architectural changes update architecture docs; meaningful work updates
  `docs/state/current.md`.
- Never call behavior verified unless the stated checks were run. Report any
  remaining code/documentation drift.
