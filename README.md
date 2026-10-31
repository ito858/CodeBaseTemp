# Documentation-Driven OpenCode + OpenSpec Template

This repository is a durable project-memory template for OpenCode. It uses plain
Markdown, YAML, and Git; it does **not** require the OpenSpec CLI to be installed.

## Clone

```sh
git clone https://github.com/ito858/CodeBaseTemp.git
cd CodeBaseTemp
```

## Start here

1. Replace the placeholders in `docs/PROJECT.md` and `docs/product/`.
2. Read `docs/INDEX.md` for the map and authority model.
3. Put unstructured requirements in `docs/inbox/`, then run `/ingest <path>` in
   OpenCode.
4. Review the resulting proposal before implementation.

## OpenCode commands

- `/ingest <path>` — turn raw material into a proposed, reviewable change.
- `/reconcile [scope]` — identify conflicts and documentation drift.
- `/opsx/propose <change-name>` — create an OpenSpec-compatible change folder.
- `/opsx/apply <change-name>` — implement approved tasks and verify them.
- `/opsx/archive <change-name>` — sync specs and archive a completed change.
- `/sync-docs [scope]` — maintain affected durable records.
- `/resume` — reload the minimum handoff context for a new session.

## Optional OpenSpec CLI

The `openspec/` layout and artifacts are compatible with OpenSpec. If you later
install its CLI, run `openspec init` or `openspec update` deliberately and review
the generated workflow files before committing them.
