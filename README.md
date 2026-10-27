# Agent workflow template

Reusable AI coding-agent setup for Cursor / Claude Code (and similar).

Clone this repo as a new project skeleton, or copy the files into an existing repo so the team shares one workflow.

## What's included

| Path | Role |
|---|---|
| `AGENTS.md` | Agent map: scope, key files, default acceptance |
| `CLAUDE.md` | Same map for Claude Code (kept in sync with `AGENTS.md`) |
| `.cursor/rules/llm-agent-safety.mdc` | Always-on safety (secrets, destructive shell, HITL) |
| `.cursor/rules/project.md` | Project acceptance commands + bans (fill in) |
| `docs/spec/task_TEMPLATE.md` | One-task brief template agents `@` mention |

## New project

```bash
gh repo create my-app --private --template wmsing/agent-workflow-template --clone
# or:
git clone https://github.com/wmsing/agent-workflow-template.git my-app
cd my-app
rm -rf .git && git init
```

Then edit placeholders marked `TODO` in `AGENTS.md`, `CLAUDE.md`, and `.cursor/rules/project.md`.

## Existing project

Copy into the repo root:

- `AGENTS.md`, `CLAUDE.md`
- `.cursor/rules/`
- `docs/spec/task_TEMPLATE.md` (optional; keep writing `docs/spec/task_*.md` per feature)

Commit so every teammate and every agent session gets the same map.

## MCP (optional)

MCP servers are configured **locally** (Cursor Settings / Claude Desktop) — do **not** commit tokens.

Document which MCPs this project expects in `AGENTS.md` → **MCP** section (e.g. GitHub for PRs, browser for UI checks). Each person connects their own account.

## Team use

1. These files live in git → one source of truth.
2. Feature work goes through `docs/spec/task_*.md` (goal / non-goals / files / acceptance).
3. Default tests = **scoped** to the change; full suite only when someone asks.

## Resume / interview one-liner

*Designed a reusable agent-ready repo template (`AGENTS.md` / Cursor rules / task specs) so coding agents follow shared scope, file maps, and scoped acceptance without re-prompting.*
