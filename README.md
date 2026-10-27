# Agent workflow template

Day-to-day Cursor / Claude Code setup I use in real repos: short agent map, safety rules, and per-feature briefs with **executable** acceptance.

## What's included

| Path | Role |
|---|---|
| `AGENTS.md` | Short agent map (source of truth). Edit this only. |
| `CLAUDE.md` | Symlink → `AGENTS.md`. Windows: copy if the link fails. |
| `.cursor/rules/llm-agent-safety.mdc` | Always-on safety text (pair with deny/hooks for hard bans) |
| `.cursor/rules/project.mdc` | Acceptance commands + bans (fill in) |
| `docs/spec/task_TEMPLATE.md` | Brief → real `task_*.md` that agents `@` |

## Workflow

1. **Start** — New: clone, fill `TODO`s. Existing: root `AGENTS.md` + `.cursor/rules`.
2. **Brief** — Unclear: brainstorm with the agent → write `task_xxx.md`, then implement in a **fresh** session. Clear non-trivial work: write the brief and `@` it.
3. **Run** — `@` brief + files/screenshots/command output the agent cannot see in code. Stay inside the brief.
4. **Accept** — Executable checks (scoped test / lint / build) until green; full suite only when asked.
5. **Close** — Keep the brief; next piece gets a new `task_*.md`. `/clear` or new chat between unrelated work.

One-line tweaks: skip the brief. MCP: local only, never commit tokens.

**Hard rules** (no `.env`, must format, etc.): don’t rely on prose alone — Cursor rules + Claude Code [deny settings / hooks](https://code.claude.com/docs/en/best-practices#enforce-the-rules-that-cant-have-exceptions). Path-only rules → `.claude/rules/` or Cursor globs; repeatable procedures → [skills](https://code.claude.com/docs/en/best-practices#put-team-procedures-in-skills).

## New project

```bash
git clone https://github.com/wmsing/agent-workflow-template.git my-app
cd my-app && rm -rf .git && git init
```

Fill `TODO`s in `AGENTS.md` and `.cursor/rules/project.mdc`.

## Existing project

Copy `AGENTS.md`, `CLAUDE.md` (symlink or copy), `.cursor/rules/`, and optionally `docs/spec/task_TEMPLATE.md`. Commit so everyone gets the same map.

## Aligned with

Extracted from live repos, then checked against:

| What we do | Matches |
|---|---|
| `AGENTS.md` overview / build-test / style / testing / security / extras | [agents.md](https://agents.md/) “Cover what matters” |
| Short map; only what code can’t show; scoped checks | [Claude Code best practices](https://code.claude.com/docs/en/best-practices) |
| Spec/brief → fresh implement; pass/fail checks; hooks for no-exception rules | Same Claude BP pillars (visibility, verifiable checks, deterministic enforce) |
| `.cursor/rules` + `AGENTS.md` | [Cursor Rules](https://cursor.com/docs/rules) |
