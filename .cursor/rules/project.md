# Project rules

## Acceptance (after code changes, run at least one)

Default: only tests **related to this change**. Do **not** run the full suite unless the user asks.

```bash
# TODO: project lint + scoped test
# npm run lint && npm test -- related.test.ts
# cd backend && uv run ruff check . && uv run pytest -q tests/test_related.py
```

## Hard bans

- Do not commit or let the agent read real `.env*`, keys, or production credentials.
- Do not change production config / auth / payment wiring without an explicit ask.
- DB migrations: propose up/down plan before editing.

## Style

- Follow existing lint/format config; match neighboring files when none exists.
- Prefer small diffs; no drive-by refactors.
