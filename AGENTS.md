# Agent map

Instructions for coding agents. Humans use `README.md`; agents use this file ([AGENTS.md](https://agents.md/) format).

## Project overview

<!-- TODO: 1–3 sentences: what this repo is, main stack, high-level layout -->

- Stack: <!-- e.g. Python/FastAPI + React, Next.js, Flutter… -->
- Layout: <!-- e.g. `backend/`, `frontend/`, `docs/spec/` -->
- Key paths: see **Key files** below
- Non-trivial work: prefer a `docs/spec/task_*.md` brief and `@` it in chat

## Build and test commands

```bash
# TODO: install / run / lint / test for this project
# install: …
# dev: …
# lint: …
# test (scoped example): …
# test (full suite — only when the user asks): …
```

**Default:** run only tests related to the change (paths you touched or the brief names). Do **not** run the full suite unless the user explicitly asks.

## Code style guidelines

<!-- TODO: only project-specific rules agents cannot infer from lint/config -->

- Follow existing lint/format config; match neighboring files when none exists
- Prefer small diffs; no drive-by refactors
- <!-- e.g. TypeScript strict, quote style, functional patterns… -->

## Testing instructions

- Add or update tests for behavior you change
- Prefer a single focused test file / filter over the whole suite
- <!-- TODO: CI path, e.g. `.github/workflows/…`; how to run one test -->
- Match any gold sample or checklist in the brief or latest chat

## Security considerations

- Do **not** read or commit real `.env*` / secrets / credentials
- Do **not** modify auth, payment, or production secret wiring unless the user names the file and confirms
- DB / schema migrations need an up/down plan before any change
- Irreversible actions (force-push, deploy, send money/mail, install new MCP) need explicit user confirmation first
- See also `.cursor/rules/llm-agent-safety.mdc`

## Extra instructions and workflow

### Scope

Only implement what the user names in chat and/or in a `docs/spec/task_*.md` they `@` mention. Do **not** expand scope (scrapers, new services, broad refactors) unless the brief says so. One-off details stay in chat; the brief wins over vague chat when both exist.

### Default workflow

1. Read `README.md`, this file, `.cursor/rules/project.md`, and the relevant `docs/spec/task_*.md`
2. Change only the key files the brief names (or the smallest set needed)
3. Add or update tests for behavior you change
4. Run scoped acceptance commands (above)

### Key files

<!-- TODO: list real entry / API / UI / domain paths -->

- Specs / briefs: `docs/spec/task_*.md`
- Rules: `.cursor/rules/project.md`, `.cursor/rules/llm-agent-safety.mdc`

### Git / PR (optional)

<!-- TODO: commit message format, PR checklist, branch naming — or delete this subsection -->

### MCP

<!-- TODO: expected connectors; leave empty if none -->

- Allowed (when connected locally): e.g. GitHub (PRs), browser (UI check)
- Forbidden: payment/trading send, reading production secrets, installing new MCP without user confirmation

### Monorepo

If needed, add nested `AGENTS.md` files under packages; the closest file to the edited path wins ([agents.md](https://agents.md/)).
