# s69-mc-codex heartbeat fail-soft gate

Recorded: 2026-06-20 China time
Owner/prefix: s69-mc-codex-

## Fact

Batch 98 hardened long-run writer heartbeat persistence.

- `RunHeartbeat.touch()` now catches heartbeat write, replace, and JSON serialization failures.
- Failure returns `heartbeat_write.ok=false`, `reason=heartbeat_write_failed`, `path`, `tmp_path`, and bounded `write_error`.
- Temporary heartbeat files are removed best-effort on failure.
- Checkpoint stat is wrapped by `_safe_checkpoint_state()`, returning `checkpoint.reason=checkpoint_stat_failed` instead of interrupting the runner.
- `run_matrix`, `run_drive`, and `run_chunk` only call heartbeat for monitoring and do not use heartbeat results for story verdict, gate, promotion, or S/40/80 claims.

## Evidence

- Project: `G:\codex-project\s69-mc-codex`
- Branch: `s69-mc-codex`
- Remote push target: `octosgh/s69-mc-codex`
- Code commit: `bf3ad92ca fix(writer): make heartbeat writes fail soft`
- Log commit: `a96ee8946 docs: record heartbeat fail-soft gate`
- Subagent review: `Peirce the 2nd` APPROVE, 0 findings.
- Tests:
  - `python -m pytest services\writer\tests\test_liveness.py services\writer\tests\test_run_matrix_promotion.py services\writer\tests\test_drive_runner.py services\writer\tests\test_chunk_runner.py -q` -> 14 passed
  - `python -m pytest services\writer\tests -q` -> 354 passed, 2 skipped
  - `python -m pytest services\determ\tests -q` -> 61 passed
  - `python -m pytest services\review\tests -q` -> 9 passed
  - `py_compile` passed for liveness and runner modules.
- `codegraph sync` completed / already up to date.

## Boundary

No live provider writing or review was started. This is a monitoring persistence hardening gate only, not a 40/80 episode S-grade or zero-hard-collapse production claim.
