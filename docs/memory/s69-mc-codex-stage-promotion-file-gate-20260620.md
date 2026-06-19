# s69-mc-codex stage promotion file gate

Recorded: 2026-06-20 01:39 China time
Owner/prefix: `s69-mc-codex-`

Project/worktree: `G:\codex-project\s69-mc-codex`
Branch: `s69-mc-codex`
Commit: `ed37f98e fix(writer): harden stage promotion files`

## Lesson

The 80-episode previous-stage S proof must fail closed when a promotion manifest file entry is not a regular file. Directly hashing a directory or unreadable path can hard-crash launch preflight.

## Behavior

- Non-file promotion manifest file entry: `promotion_file_not_file`.
- Hash read `OSError`: `promotion_file_unreadable`.
- Missing/sha mismatch/sha missing behavior remains unchanged.

## Evidence

- Code: `services/writer/octos_writer/stage_promotion.py`
- Regression: `services/writer/tests/test_launch_preflight.py::test_launch_preflight_blocks_80_when_promotion_file_path_is_directory`
- Verification: launch_preflight previous-stage targeted `11 passed`; writer full `265 passed, 2 skipped`; determ `56 passed`; review `9 passed`.
- Subagent: `Franklin` APPROVE, 0 findings.

No live provider was started and no 40/80 quality claim was made.
