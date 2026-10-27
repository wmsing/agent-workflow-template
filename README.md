# Agent workflow template

Day-to-day Cursor / Claude Code setup I use in real repos: agent map, safety rules, and per-feature briefs. Clone for a new project, or copy into an existing one so the team shares one workflow.

## What's included

| Path | Role |
|---|---|
| `AGENTS.md` | Agent map (source of truth). Edit this only. |
| `CLAUDE.md` | Symlink → `AGENTS.md`. Windows: copy if the link fails. |
| `.cursor/rules/llm-agent-safety.mdc` | Always-on safety (secrets, destructive shell, HITL) |
| `.cursor/rules/project.md` | Acceptance commands + bans (fill in) |
| `docs/spec/task_TEMPLATE.md` | Brief template → real `task_*.md` that agents `@` |

## Workflow

1. **Start** — New: clone this repo, fill `TODO`s. Existing: put `AGENTS.md` + `.cursor/rules` at the root.
2. **Brief** — Non-trivial work: copy `task_TEMPLATE.md` → `task_xxx.md` (goal, non-goals, files, acceptance).
3. **Run** — `@` the brief in Cursor / Claude Code; agent follows map + brief only.
4. **Accept** — Scoped tests for the change; full suite only when asked.
5. **Close** — Keep the brief as history; next piece gets a new `task_*.md`.

One-line tweaks: skip the brief. MCP: connect locally, never commit tokens; list expected connectors under **MCP** in `AGENTS.md`.

## New project

```bash
git clone https://github.com/wmsing/agent-workflow-template.git my-app
cd my-app && rm -rf .git && git init
```

Fill `TODO`s in `AGENTS.md` and `.cursor/rules/project.md`.

## Existing project

Copy `AGENTS.md`, `CLAUDE.md` (symlink or copy), `.cursor/rules/`, and optionally `docs/spec/task_TEMPLATE.md`. Commit so everyone gets the same map.
