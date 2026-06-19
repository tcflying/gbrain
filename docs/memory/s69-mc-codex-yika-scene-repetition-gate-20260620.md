# s69-mc-codex Yika scene-level repetition gate

Recorded: 2026-06-20 China time
Owner/prefix: `s69-mc-codex-`

## Rule

Official 一卡 validator must hard-fail repeated episode assets beyond title/core/card repetition: `本集名场面`, scene bodies, `△` action cues, dialogue lines, and final subtitle cards.

## Evidence

- Project repo: `G:\codex-project\s69-mc-codex`.
- Branch: `s69-mc-codex`.
- Commit: `b7952ef52 fix(writer): reject repeated yika scene assets`.
- Code: `services/writer/octos_writer/yika_format.py`, `services/writer/tests/test_yika_format.py`.
- Tests: yika_format 35 passed; writer 289 passed / 2 skipped; determ 61 passed; review 9 passed.
- Subagent review: `Boyle` requested changes; `Schrodinger` approved after fixes.
