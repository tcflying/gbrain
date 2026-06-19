# s69-mc-codex stop-clear evidence gate

Recorded: 2026-06-19 China time
Owner/prefix: `s69-mc-codex-`

Project commit:
- Repo/worktree: `G:\codex-project\s69-mc-codex`
- Branch/remote: `s69-mc-codex` -> `octosgh/s69-mc-codex`
- Commit: `e2f15620 fix(writer): stop and clear planned runs on failure`

Operational rule:
- Clean writer failure evidence must not only claim planned queue cleared; it must invalidate or archive resumable checkpoints that could otherwise restart failed work.

Implementation:
- Added `services/writer/octos_writer/stop_clear.py`.
- `run_matrix.py`, `run_drive.py`, and `run_chunk.py` write `*_stop_clear_evidence.json` on config preflight, provider preflight, final gate, delivery, or manifest failure.
- Stop evidence includes `future_launch_allowed=false`, `planned_queue_cleared=true`, completed/remaining episodes, final gate/provider preflight summary, checkpoint status, and checkpoint actions.
- Existing checkpoint files are archived to `.stopped-<utc>`.
- `run_chunk.py` stops after a failed chunk size and records `remaining_chunk_sizes_cleared`.
- `drive.drive()` defaults to `stop_on_failure=True`; probe callers may set `stop_on_failure=False`.

Verification:
- stop/drive/chunk/matrix targeted tests: 15 passed.
- Writer offline suite: 115 passed, 7 deselected.
- Determ suite: 35 passed.
- Review suite: 9 passed.
- Subagent `Pasteur` final review: 0 issues / LGTM.

Remaining:
- Before first 40-episode production writing, final readiness review must prepare real `OCTOS_BRIEF_FILE`, fresh provider quota proof, route-pressure clear state, valid-generation manifest, three-review entry, and export destination evidence.
