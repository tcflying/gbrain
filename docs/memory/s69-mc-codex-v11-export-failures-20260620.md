# s69-mc-codex V11 export failure hardening

Recorded: 2026-06-20 01:53 China time
Owner/prefix: `s69-mc-codex-`

Project/worktree: `G:\codex-project\s69-mc-codex`
Branch: `s69-mc-codex`
Commit: `1459de10 fix(writer): harden v11 export failures`

## Lesson

V11 A+ mc-codex export must fail structurally on output-path problems. It must not hard-crash after A+ review and must not claim success after a partial write failure.

## Behavior

- Output directory unavailable: `v11_export_dir_unavailable`, `written=[]`.
- File write failure: `v11_export_write_failed`, `failed_path`, and only already-written paths in `written`.
- Normal A+ export remains one script plus three reviews: MiniMax-M3-think, GLM-5.2-think, GPT-5.5综合. Claude is not exported.

## Evidence

- Code: `services/writer/octos_writer/delivery.py`
- Regression: `services/writer/tests/test_v11_delivery.py::test_write_v11_mc_codex_exports_reports_output_dir_conflict`
- RED proof: old code raised `FileExistsError` when `out_dir` already existed as a file.
- Verification: V11/delivery targeted `9 passed`; writer full `267 passed, 2 skipped`; determ `56 passed`; review `9 passed`.
- Subagent: `Ampere` APPROVE, 0 findings.

No live provider was started and no production/S/40/80 quality claim was made.
