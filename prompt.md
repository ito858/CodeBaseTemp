Your requirement changes my recommendation substantially.

You're not really looking for an OpenCode starter kit anymore. You're looking for a persistent, documentation-driven engineering system where the codebase accumulates knowledge as the project evolves.

Your guiding principle:

> Prompting is temporary; Structure is permanent.

I would extend that into three rules:

1. Prompts are input, not the source of truth. Rough ideas, lengthy explanations, and unstructured requirements should be converted into durable files.
2. The repository is the project memory. Requirements, architecture, decisions, implementation progress, and unresolved questions survive across AI sessions.
3. Documentation maintenance is part of implementation. When code changes, the agent updates the corresponding structured records, rather than leaving them to drift.

This is closer to spec-driven development + living documentation + persistent agent memory than to a typical multi-agent framework.

## 1. GitHub projects that better match this philosophy

[Spec-Driven Development is Here :- And It Changes How We Build with AI](https://images.openai.com/static-rsc-4/QDGt6m_DXd9i_-moFMtzYG6dzK0XlcUTeEA24hMTpH8yTZ9HnSGSGDPJp3HyXfxomERQkmeCy2OdjQCrLohHbqYhcKDubem-HSKTNpWINpBS9QFgLjaWuyUjqUbpWTJnCNVQBVyIVtb0oNhapSz2r0pOhsXB-kX37RNXYjoa_ec?purpose=inline)

[github/spec-kit](https://github.com/github/spec-kit?utm_source=chatgpt.com)

Strong fit

Organizes development into durable specifications, plans, task lists, principles, and implementation workflows. Especially relevant for transforming messy requirements into structured files.

Best for: turning informal prompts into formal specifications.



[image](https://www.google.com/s2/favicons?domain=https://github.github.com\&sz=32)

Spec Kit Documentation+1



[Releases · Fission-AI/OpenSpec · GitHub](https://images.openai.com/static-rsc-4/t7O_yZPK1z1oPq89WsIK93nj0BCQkCYDSU8pfqu7jvO6jUCakjTyWlD46awPdNAmt7ISK2pr_iqLB9_zLMIDNNojFai9gYMoOzCzgsnaMgmrOaSllcNpFcMIkZVETdkLrd9EAnRUwQMDTKuT2m1Uy_VCVEJvIXj9W_3fM780YzE?purpose=inline)

[Fission-AI/OpenSpec](https://github.com/Fission-AI/OpenSpec?utm_source=chatgpt.com)

Best overall match

Maintains canonical specifications, active change proposals, design documents, tasks, and historical change archives. Includes mechanisms to synchronize evolving requirements into the main specifications.

Best for: maintaining project knowledge across many iterations.



[image](https://www.google.com/s2/favicons?domain=https://github.com\&sz=32)

GitHub+1



[GSD - Get Shit Done | AI Coding Framework](https://images.openai.com/static-rsc-4/u6yVYHy4gXlaqBdaTxw-9ZYiAPp0lnpoYnVKT88zjpYaDl0Ex6J4afz5dRzp7BYkMpO50uexeZmPJmNVUpghfPqvfGS8EEBMYr8OG80plKAPLWzWXEWnUvvxQK3Hod3oGpG3qHkls2-A6W-gSJbej6wo7I7FxKy6mHtMlaZXUtk?purpose=inline)

[gsd-build/get-shit-done](https://github.com/gsd-build/get-shit-done?utm_source=chatgpt.com)

Emphasizes persisted planning context, roadmaps, phases, and handoffs across development sessions.

Best for: resuming work reliably after context resets.

My preferred foundation would now be OpenSpec, supplemented with a lightweight project knowledge base and an intake process for long, unstructured prompts.

The key distinction: OpenSpec handles change specifications well, but I would add a separate documentation layer for project-wide context, raw inputs, architecture, and operational knowledge.

## 2. Proposed architecture: a living project knowledge base

Here's the structure I would actually build for you.

Repository structure

&#x20;Copy

project/\
├── AGENTS.md\
├── opencode.json\
├── .opencode/\
│   ├── commands/\
│   │   ├── ingest.md\
│   │   ├── reconcile.md\
│   │   ├── implement.md\
│   │   ├── sync-docs.md\
│   │   └── resume.md\
│   └── skills/\
│       └── knowledge-maintenance/SKILL.md\
├── docs/\
│   ├── INDEX.md\
│   ├── PROJECT.md\
│   ├── product/\
│   │   ├── vision.md\
│   │   ├── requirements.md\
│   │   └── glossary.md\
│   ├── architecture/\
│   │   ├── overview\.md\
│   │   ├── data-model.md\
│   │   └── integrations.md\
│   ├── decisions/\
│   │   └── ADR-0001-example.md\
│   ├── features/\
│   │   └── feature-name.md\
│   ├── operations/\
│   │   └── deployment.md\
│   ├── inbox/\
│   │   └── raw-input-001.md\
│   └── state/\
│       ├── current.md\
│       └── open-questions.md\
├── openspec/\
│   ├── config.yaml\
│   ├── specs/\
│   └── changes/\
└── src/

The most important thing isn't the number of Markdown files. It's that every kind of knowledge has a clearly defined home and lifecycle.

| Layer                | Purpose                                    | Maintenance policy                  |
| -------------------- | ------------------------------------------ | ----------------------------------- |
| `docs/inbox/`        | Long, messy, unprocessed inputs            | Preserve original content           |
| `docs/product/`      | Goals, domain definitions and requirements | Update when intent changes          |
| `openspec/specs/`    | Canonical behavioral specifications        | Sync after approved changes         |
| `docs/architecture/` | Current technical design                   | Update when architecture changes    |
| `docs/decisions/`    | Why important decisions were made          | Append new ADRs, supersede old ones |
| `docs/state/`        | Current progress, blockers and handoff     | Update after each significant task  |
| `AGENTS.md`          | Rules governing agent behavior             | Keep concise and stable             |

## 3. The workflow you're describing

Raw ideas and long prompts

Paste into docs/inbox/ or reference an existing file

/ingest

Extract requirements, constraints, questions and conflicts

/reconcile

Compare with existing specs, decisions and code

/implement

Plan, develop and verify the approved change

/sync-docs

Reconcile canonical specs, architecture and progress

Durable repository knowledge

Git versioned, reviewable and reusable across sessions

These `/ingest`, `/reconcile`, `/implement`, `/sync-docs` and `/resume` commands would be custom commands in your template, not existing built-in OpenCode features.

### Example: your long, unorganized prompt

Suppose you're building a reservation system. You write 3,000 words covering cancellations, time zones, availability, payments, permissions and edge cases, with some contradictions.

Rather than pasting everything into OpenCode's chat window, you create:

`docs/inbox/2026-10-31-reservations.md`

Then, inside OpenCode:

```
/ingest docs/inbox/2026-10-31-reservations.md
```

The agent should:

1. Preserve the original file without rewriting it.
2. Identify distinct functional and nonfunctional requirements.
3. Check existing specifications for duplication and contradictions.
4. Draft structured updates in an active change proposal.
5. Record ambiguities as questions instead of inventing answers.
6. Ask you to approve material requirement changes before treating them as authoritative.

The result might be a new `openspec/changes/reservation-workflow/` containing a proposal, spec deltas, design and tasks.

This prevents your original prompt from becoming the only place where important requirements exist.

## 4. Make documentation maintenance mandatory

Here is the core policy I'd put in your root `AGENTS.md`.

```
# Project Knowledge Protocol

## Principle
Prompting is temporary; structure is permanent.

The repository is the authoritative source of
project knowledge. Conversation history is not.

## Before modifying code
1. Read docs/INDEX.md.
2. Locate the relevant feature specifications.
3. Read applicable architectural decisions.
4. Check docs/state/current.md.
5. Identify conflicts between the request,
   existing documentation, and implementation.

## When receiving unstructured requirements
1. Preserve source material in docs/inbox/.
2. Extract atomic, testable requirements.
3. Separate confirmed facts from assumptions.
4. Record unresolved questions explicitly.
5. Propose structured changes.
6. Never silently override established decisions.

## During implementation
1. Follow approved specifications.
2. Keep implementation tasks current.
3. Record architectural decisions when needed.
4. Do not mark untested behavior as verified.

## After implementation
1. Update affected canonical specifications.
2. Update affected architecture documentation.
3. Update docs/state/current.md.
4. Record unresolved issues and follow-up work.
5. Report any remaining code/documentation drift.

## Documentation quality
- Prefer editing existing canonical files.
- Avoid duplicating requirements across files.
- Link to authoritative specifications.
- Preserve decision history.
- Avoid speculative claims presented as facts.
- Keep AGENTS.md concise.
```

This policy is enforceable as an agent workflow, but instructions alone do not guarantee compliance. I would also add automated checks and a CI requirement to reduce documentation drift.

For example, a feature-modifying pull request could be required to include a specification update or an explicit explanation that no behavioral documentation changed.

## 5. Avoid a new problem: documentation overload

A large collection of permanent files can become as disorganized as the original prompts.

I would implement three protections.

First, progressive context loading. OpenCode reads a short `AGENTS.md` and `docs/INDEX.md` initially, then loads relevant specs and architecture documents only when needed. OpenCode supports project instructions and additional instruction files, so you don't need to put the entire knowledge base into every model request.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://opencode.ai\&sz=32)

OpenCode+1



Second, explicit document authority. Define which file wins when information conflicts:

Recommended authority hierarchy

Approved specifications and decisions

Current architecture and implementation records

Active change proposals

Raw ideas and unprocessed prompts

Actual code remains evidence of implemented behavior, even when it contradicts a specification. The agent should flag that contradiction rather than silently declaring either version correct.

Third, maintain documents by events, not indiscriminate rewriting. A database schema change should trigger a data-model review. A functional behavior change should trigger a specification review. A new architectural decision should produce an ADR. Routine code cleanup should not rewrite the whole knowledge base.

## 6. Final framework recommendation

| Capability                                | Best foundation                  |
| ----------------------------------------- | -------------------------------- |
| Raw prompts → structured requirements     | GitHub Spec Kit concepts         |
| Ongoing specifications and change history | OpenSpec (OPSX)                  |
| Persistent session state and handoffs     | Lightweight custom `docs/state/` |
| Project knowledge and navigation          | Custom `docs/INDEX.md`           |
| Automatic documentation maintenance       | OpenCode commands, skills and CI |
| Long-term portability                     | Plain Markdown, YAML and Git     |

One caveat: the earlier `gsd-build/get-shit-done` repository was archived on June 26, 2026. I'd study its context-management ideas rather than make that archived repository a dependency.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://github.com\&sz=32)

GitHub



My recommendation is a custom OpenCode + OpenSpec template, not another large agent framework. Keep the workflow simple, make documents the durable output, and let the agent continuously reconcile requirements, decisions and code.

