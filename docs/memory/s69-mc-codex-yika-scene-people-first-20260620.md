# s69-mc-codex official_yika scene people line order gate

Recorded: 2026-06-20 01:18 China time
Owner/prefix: `s69-mc-codex-`

Codex tightened official_yika scene block ordering in `G:\codex-project\s69-mc-codex`.

Evidence:
- Project commit: `3f84a078 fix(writer): require yika scene people first`
- Branch/push target: `s69-mc-codex` -> `octosgh/s69-mc-codex`
- CodeGraph sync completed after commit.

Official reference boundary:
- Read-only extraction of `C:\Users\datoo\Desktop\h红果与案例\《锦衣羽刃》一卡(1).docx` showed completed scenes put `人物：` immediately after the scene heading and include `△` action/visual cues.
- The same extraction showed episode 7 scene 1 has no dialogue lines, so per-scene dialogue must not become a hard official_yika gate.

Implementation:
- `services/writer/octos_writer/yika_format.py` now emits hard issue `scene_people_line_order` when a strict scene block has a `人物：` line but the first scene body line is not `人物：`.
- Missing people remains `scene_people_line_missing`, keeping missing and ordering failures distinct.

Validation:
- RED proved old code accepted a scene with `△` before `人物：`.
- scene/order/reference targeted: 4 passed.
- official_yika/delivery/v11/runner targeted: 72 passed.
- Writer tests: 255 passed, 2 skipped.
- Determ tests: 56 passed.
- Review tests: 9 passed.
- Changed-file `py_compile` passed.
- `git diff --check` passed with only CRLF warnings.

Review:
- Subagent `Euclid` read-only review: APPROVE, 0 CRITICAL/HIGH/MEDIUM/LOW findings.

No live provider writing or review was started.
