# s69-mc-codex complete Yika pipeline audit

Recorded: 2026-06-19 China time
Owner/prefix: `s69-mc-codex-`

## Source checked

- CodeGraph first, then current source files under `G:\codex-project\s69-mc-codex`.
- Historical context: `G:\claude-project\octos-MC\6.18.md` and Claude session
  `C:\Users\datoo\.claude\projects\G--claude-project-multica\c5350ae2-3a45-4a62-8132-866477e1e160.jsonl`.

## Current code truth

- `services/writer/octos_writer/run_matrix.py` is the current whole-card attempt:
  per-episode best-of-N, checkpoint, and final whole-card V11 score.
- `services/writer/octos_writer/drive.py` is a per-episode write-gate-repair loop.
- `services/writer/octos_writer/chunk.py` is run-size/chunk comparison, not final
  delivery.
- `services/writer/octos_writer/repair.py` is the tiered repairer, but it lacks
  direct test coverage and chunk scope is not a true cross-episode repair yet.
- `services/review/octos_review/dispatch.py` keeps D review advisory only; B/determ
  remains the binding gate.
- `services/review/octos_review/v11.py` is whole-card V11 final judgement.
- Legacy `services/determ/_legacy/tools/qa/script_drama_writer.py` contains the
  closer DOCX-style writer/renderer functions `write_drama_book()` and
  `build_drama_docx()`, but it is not integrated into the clean writer main path.

## Test result

- `services/writer`: 19 passed.
- `services/review`: 9 passed.
- `services/determ`: 24 passed, 1 failed.
- Failure: `drama_regression_cases.py` cannot find
  `services/determ/_legacy/data/config/drama_script_spec.json`.
- Claude tree has this missing spec at
  `G:\claude-project\octos-MC\services\determ\_legacy\data\config\drama_script_spec.json`.

## Operational conclusion

Do not claim this worktree has a ready complete Yika final-delivery pipeline yet.
Before production writing, close the delivery chain:

1. Restore/rebuild the missing drama spec against the official `《锦衣羽刃》一卡(1).docx`.
2. Recalibrate format gate and episode splitting against official sample structure.
3. Unify writer/matrix/chunk/legacy renderer into one final delivery path.
4. Add repair/matrix/chunk tests.
5. Produce one script plus three reviews under `C:\Users\datoo\Desktop\v11\mc-codex`
   only after source-bound review and V11 evidence exist.

## Evidence

- Project log commit: `529af8f4 docs: record yika pipeline code audit`.
