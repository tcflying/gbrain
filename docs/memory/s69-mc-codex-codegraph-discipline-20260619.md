# s69-mc-codex CodeGraph and scoped update discipline

Recorded: 2026-06-19 China time
Owner/prefix: `s69-mc-codex-`

## Rule

For `G:\codex-project\s69-mc-codex`, large code changes must inspect
CodeGraph first. Small, narrow changes such as docs/log/todo edits do not
need a CodeGraph lookup before editing.

After any update, Codex must make a scoped commit, push branch
`s69-mc-codex`, and refresh the local graph with `codegraph sync` or an
equivalent update command.

## Boundary

This is project-local to the `s69-mc-codex` worktree/branch. Do not move it
into global `C:\Users\datoo\.codex\AGENTS.md`.

## Evidence

- Project commit: `b236a4fc docs: record codegraph update discipline`.
- Push target: `octosgh/s69-mc-codex`.
- CodeGraph status after sync: `Index is up to date`, 2,088 files,
  32,439 nodes, 111,002 edges.
