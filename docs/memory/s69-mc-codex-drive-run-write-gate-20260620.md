# s69-mc-codex drive run write gate

Recorded: 2026-06-20 China time
Owner/prefix: `s69-mc-codex-`

Project: `G:\codex-project\s69-mc-codex`
Branch/push target: `s69-mc-codex` -> `octosgh/s69-mc-codex`

## Lesson

Runner result JSON files are production proof artifacts. `drive_run.json` write failures must be handled as route/proof failures that block post-generation review and return 2, not as uncaught filesystem crashes.

## Fix and evidence

- Code commit: `f2ee40743 fix(writer): fail drive run writes closed`
- Log commit: `90b6e2ae6 docs(log): record drive run write gate`
- Files: `services/writer/run_drive.py`, `services/writer/tests/test_drive_runner.py`, `619.md`, `619todo.md`
- Change: `drive_run.json` writes now use `_write_json_report(..., result_key="run_json_write")`.
- Initial write failure blocks post-generation review with `drive_run_json_write_failed`.
- Post-review rewrite failure returns 2 and writes stop-clear with `run_json_write` evidence.
- `run_json_failed_once` and `run_json_failure` keep heartbeat/log/return code failed and preserve the original write error.

## Verification

- drive_runner: 2 passed.
- Targeted drive/provider/stop-clear/post-review combo: 70 passed.
- Writer suite: 334 passed, 2 skipped.
- Determ suite: 61 passed.
- Review suite: 9 passed.
- `py_compile run_drive.py`: passed.
- CodeGraph sync: completed / already up to date.
- Subagent review: Mill approved with 0 findings.

No live provider writing/review was started. No S/40/80 completion claim.
