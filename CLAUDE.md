# Agent map

## Scope

Only implement what the user names in chat and/or in a `docs/spec/task_*.md` they `@` mention.

Do **not** read or commit real `.env*` / secrets / credentials.
Do **not** expand scope (scrapers, new services, refactors) unless the brief says so.
DB / schema migrations need an up/down plan before any change.

One-off details stay in chat. The latest instruction in chat wins over older chat; the brief wins over vague chat when both exist.

## Default workflow

1. Read `README.md`, this file, `.cursor/rules/project.md`, and the relevant `docs/spec/task_*.md`
2. Change only the key files the brief names (or the smallest set needed)
3. Add or update tests for behavior you change
4. Acceptance: **default = only tests related to this change**. Do **not** run the full suite unless the user explicitly asks.

```bash
# TODO: replace with this project's lint + scoped test commands
# example (Python):
#   cd backend && uv sync --extra dev && uv run ruff check .
#   uv run pytest -q tests/test_thing_you_changed.py
# example (Node):
#   npm run lint && npm test -- path/to/related.test.ts
```

## Key files (repo root)

<!-- TODO: list the real paths for this project -->

- Specs / briefs: `docs/spec/task_*.md`
- Rules: `.cursor/rules/project.md`, `.cursor/rules/llm-agent-safety.mdc`
- <!-- App entry / API / UI / core domain files… -->

## MCP

<!-- TODO: list expected connectors; leave empty if none -->

- Allowed (when connected locally): e.g. GitHub (PRs), browser (UI check)
- Forbidden: trading / payment send, reading production secrets, installing new MCP without user confirmation

## Acceptance

```bash
# TODO: same commands as Default workflow §4
```

Match any gold sample or acceptance checklist in the brief or latest chat.
