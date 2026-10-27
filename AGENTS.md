# Agent map

For coding agents ([AGENTS.md](https://agents.md/)). Keep this file **short** — only what agents cannot learn by reading the code ([Claude Code](https://code.claude.com/docs/en/best-practices): meetings, deploy quirks, env that isn’t in-repo, team “don’t do X”).

## Project overview

<!-- TODO: 1–3 sentences + stack + top-level layout. No file-by-file tour. -->

- Stack / layout: …
- Non-trivial work: write `docs/spec/task_*.md` and `@` it (unclear work: brainstorm → brief in one session, implement in a fresh session)

## Build and test commands

```bash
# TODO: real commands
# install: …
# dev: …
# lint: …
# test one: …   # default
# test all: …   # only when the user asks
```

## Code style guidelines

<!-- TODO: only deltas vs lint/config. Delete bullets agents can infer. -->

- Match lint/format config and neighboring files
- Small diffs; no drive-by refactors

## Testing instructions

- Acceptance must be **executable** (test / lint / build / screenshot checklist) — not “looks done”
- Prefer one focused test filter; update tests for behavior you change
- <!-- TODO: CI path; how to run a single test -->

## Security considerations

Prose reminders only. **Hard bans** (no `.env`, no force-push, etc.) must also be enforced in tool settings / hooks / deny rules — see `.cursor/rules/llm-agent-safety.mdc` and, for Claude Code, Settings deny + Hooks.

- No real `.env*` / secrets in context or commits
- No auth/payment/prod secret wiring without an explicit named ask
- Migrations: up/down plan before editing
- Irreversible actions need explicit user confirmation

## Extra instructions and workflow

1. Read this file, `.cursor/rules/project.mdc`, and any `@` brief
2. Change only what the brief / user named
3. Run scoped checks until green
4. Full suite only when asked

**Key files:** <!-- TODO --> `docs/spec/task_*.md`, `.cursor/rules/`

**MCP:** connect locally; never commit tokens. <!-- TODO: allowed / forbidden connectors -->

**Git/PR:** <!-- TODO or delete -->

**Monorepo:** nested `AGENTS.md` (closest wins). Claude Code: path-scoped `.claude/rules/`; repeatable team procedures → `.claude/skills/` ([skills](https://code.claude.com/docs/en/best-practices#put-team-procedures-in-skills)).
