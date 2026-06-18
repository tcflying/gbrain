# s69-mc-codex provider concurrency caps

Recorded: 2026-06-19 China time
Owner/prefix: `s69-mc-codex-`

## User rule

For this Codex lane, future provider use should cap concurrent tasks at:

- MiniMax/MMX: max 6
- GLM: max 2
- Codex: max 2

When quality gates, quota, route pressure, and machine stability allow, keep
available slots as full as practical. Do not underuse provider slots merely out
of habit, but do not exceed safety, evidence, or route-pressure limits.

## Scope

- Project worktree: `G:\codex-project\s69-mc-codex`
- Branch: `s69-mc-codex`
- This is project-local provider scheduling guidance.

## Evidence

- Project commit: `8041ede3 docs: record provider concurrency caps`
- Updated project files: `AGENTS.md`, `619.md`, `619todo.md`
