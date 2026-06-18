# 239-codex-new remem V1 harness

Recorded: 2026-06-19 China time
Owner/prefix: `239-codex-new-`
Marker: `239-codex-new-remem-v1-harness-20260619`

## Decision

V1 harness for `G:\codex-project\remem` is implemented as a project-local
event replay harness. It validates article-style local reflection before any
real Codex hook installer writes `.codex/hooks.json`.

Evidence:

- Branch: `239-codex-new`
- Commit: `bba2e10 feat: add v1 event replay harness`
- Design: `G:\codex-project\remem\docs\v1-harness-design.md`
- Code: `G:\codex-project\remem\remem\harness.py`
- Tests: `G:\codex-project\remem\tests\test_v1_harness.py`

## Harness requirements

1. Replay fixture events into project-local `.remem/`.
2. Require stable `event_id` values.
3. Deduplicate repeated event ids.
4. Trigger reflection exactly at threshold boundaries.
5. Avoid completed rounds for unpaired user-only turns.
6. Keep same session id isolated across different project roots.
7. Avoid gbrain writes in V1.

## Verification

`python -m compileall remem tests` passed. `python -m unittest discover -s
tests` passed with 8 tests. CLI smoke confirmed duplicate `--event-id` returns
`recorded=false` and does not create another reflection.
