# s69-mc-codex Claude session deep audit round 3

Recorded: 2026-06-19 China time
Owner/prefix: `s69-mc-codex-`
Marker: `s69-mc-codex-claude-session-round3-20260619`

## Source material

- Project worktree: `G:\codex-project\s69-mc-codex`
- Historical handoff: `G:\claude-project\octos-MC\6.18.md`
- Claude session JSONL: `C:\Users\datoo\.claude\projects\G--claude-project-multica\c5350ae2-3a45-4a62-8132-866477e1e160.jsonl`
- Round report: `G:\codex-project\s69-mc-codex\docs\qa\claude-session-deep-audit-20260619-round3.md`

## Answer class

`partial_fix`.

Historical materials contain correct directions and multiple local fixes, but the current Codex worktree still lacks complete production closure for 一卡 writing, repair, review, export, and Multica orchestration.

## New omissions recorded

1. `matrix.py` can select least-bad not-ready prose and continue; that prose can feed `prev_tail`.
2. `chunk.py` records `split-miss` and continues; `run_chunk.py` still scores V11 and exits 0.
3. `run_drive.py`, `run_matrix.py`, and `run_chunk.py` can exit 0 when gates are not fully passed.
4. StoryBible/Postgres is optional in `drive.py`, absent in `run_drive.py`, and not proven active in matrix/chunk.
5. `repair.scope_for()` labels `missing_episode` / `multi_version` as `chunk`, but current repair still rewrites one episode.
6. `hardening.capture_miss()` / `capture_false_positive()` are manual APIs, not automatic production learning.
7. GLM/Codex provider wrappers lack contract tests; GLM/MMX HTTPError bodies are not preserved enough for route classification; Codex wrapper uses raw stdout instead of JSON events.
8. V11/format surface gates are mostly prompt-side in the clean writer, not post-generation deterministic hard gates.
9. Provider caps in `providers.py` are import-time `_CAPS` / `_SEMS`, not live-adjustable.

## Verification

- `python -m pytest services\writer\tests -q -k "not live"` -> 15 passed, 2 deselected.
- `python -m pytest services\determ\tests\test_verify_facade.py services\determ\tests\test_hardening.py -q` -> 7 passed.
- `go test ./internal/service -run Determ -count=1` from `server/` -> passed.
