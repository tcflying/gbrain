# s69-mc-codex matrix run write gate

Recorded: 2026-06-20 China time
Owner/prefix: `s69-mc-codex-`

Project: `G:\codex-project\s69-mc-codex`
Branch/push target: `s69-mc-codex` -> `octosgh/s69-mc-codex`

## Lesson

`matrix_run.json` is production evidence. Write failures there must be route/proof failures that block post-generation review and promotion. They must not become hard crashes, and they must not allow stale `base_success` or missing run evidence to pass.

## Fix and evidence

- Code commit: `54640c9df fix(writer): fail matrix run writes closed`
- Log commit: `4bdd6897b docs(log): record matrix run write gate`
- Files: `services/writer/run_matrix.py`, `services/writer/tests/test_run_matrix_promotion.py`, `619.md`, `619todo.md`
- Change: `matrix_run.json` writes now use `_write_json_report(..., result_key="run_json_write")`.
- Initial write failure blocks post-generation review with `matrix_run_json_write_failed`.
- Post-review rewrite failure blocks promotion.
- Promotion-stage final rewrite failure returns 2 and writes `matrix_run_json_write_failed` stop-clear even if promotion already wrote a stop-clear reason.
- `run_json_failed_once` and `run_json_failure` keep heartbeat/log/return code failed and preserve the original write error even if later evidence rewrite succeeds.

## Verification

- run_matrix_promotion: 6 passed.
- Targeted matrix/launch/provider/stop-clear/stage/post-review combo: 133 passed.
- Writer suite: 332 passed, 2 skipped.
- Determ suite: 61 passed.
- Review suite: 9 passed.
- `py_compile run_matrix.py`: passed.
- CodeGraph sync: completed / already up to date.
- Subagent review: Cicero findings fixed; Chandrasekhar approved with LOW stdout issue fixed.

No live provider writing/review was started. No S/40/80 completion claim.
