# s69-mc-codex review directory proof gate

Recorded: 2026-06-20 01:46 China time
Owner/prefix: `s69-mc-codex-`

Project/worktree: `G:\codex-project\s69-mc-codex`
Branch: `s69-mc-codex`
Commit: `5fd1cdba fix(writer): reject review directory proofs`

## Lesson

Previous-stage three-review proof must require real files for `post_generation_review.three_review_paths`. An existing directory is not review evidence and must not unlock 80-episode launch.

## Behavior

- Count mismatch: `three_review_paths_count_mismatch`.
- Missing path: `three_review_paths_missing`.
- Existing non-file path: `three_review_paths_not_file`.

## Evidence

- Code: `services/writer/octos_writer/stage_promotion.py`
- Regression: `services/writer/tests/test_launch_preflight.py::test_launch_preflight_blocks_80_when_previous_stage_review_path_is_directory`
- RED proof: old code returned `report["ok"] is True` for a directory review path with updated promotion manifest hashes.
- Verification: launch_preflight previous-stage targeted `12 passed`; writer full `266 passed, 2 skipped`; determ `56 passed`; review `9 passed`.
- Subagent: `Leibniz` APPROVE, 0 findings.

No live provider was started and no production/S/40/80 quality claim was made.
