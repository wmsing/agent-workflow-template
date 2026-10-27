# Agent workflow template

This is the agent setup I actually use on day-to-day coding work (Cursor / Claude Code): scope map, safety rules, and per-feature briefs so agents don’t need re-explaining every session.

Pulled out of live repos as a reusable base — clone for a new project, or copy into an existing one so the team shares the same workflow.

## What's included

| Path | Role |
|---|---|
| `AGENTS.md` | Agent map: scope, key files, default acceptance (source of truth) |
| `CLAUDE.md` | Symlink → `AGENTS.md` (Claude Code). On Windows, if the link doesn’t work, copy `AGENTS.md` to `CLAUDE.md`. |
| `.cursor/rules/llm-agent-safety.mdc` | Always-on safety (secrets, destructive shell, HITL) |
| `.cursor/rules/project.md` | Project acceptance commands + bans (fill in) |
| `docs/spec/task_TEMPLATE.md` | One-task brief; agents `@` the filled-in `task_*.md` |

Edit **only** `AGENTS.md` — don’t maintain two copies of the map.

## New project

```bash
gh repo create my-app --private --template wmsing/agent-workflow-template --clone
# or:
git clone https://github.com/wmsing/agent-workflow-template.git my-app
cd my-app
rm -rf .git && git init
```

Fill the `TODO`s in `AGENTS.md` and `.cursor/rules/project.md` (paths, lint/test commands, MCP list).

## Existing project

Copy into the repo root:

- `AGENTS.md` (+ `CLAUDE.md` symlink, or a copy on Windows)
- `.cursor/rules/`
- `docs/spec/task_TEMPLATE.md` (then keep writing real `docs/spec/task_*.md` per feature)

Commit so every teammate and every agent session reads the same map.

## MCP

MCP servers stay in local Cursor / Claude Desktop settings — never commit tokens.

If the project expects certain connectors, list them under **MCP** in `AGENTS.md` (allowed vs forbidden). Each person connects their own account.

## How we use it

1. Files live in git → shared source of truth.
2. Non-trivial features get a `docs/spec/task_*.md` (goal / non-goals / files / acceptance) before the agent runs.
3. Default acceptance = **scoped** tests for the change; full suite only when someone asks.
