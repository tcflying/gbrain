# s69-mc-codex post-review promotion proof gate

Recorded: 2026-06-20 20:15 +0800
Owner/prefix: `s69-mc-codex-`

- Repo/branch: `G:\codex-project\s69-mc-codex` / `s69-mc-codex`.
- Code commit: `262c6c2fe fix(writer): reject compromised post-review promotion proof`.
- `stage_promotion._proof_issues()` now rejects inline or persisted `post_generation_review` proof carrying `manifest_serialization_failed`, `manifest_write_failed`, `serialization_sanitized`, or matching failure reasons.
- This prevents a sanitized or write-failed `post_generation_review_manifest.json` from being accepted as 40-to-80 promotion proof.
- Tests: `test_stage_promotion.py` 20 passed; generation/launch/post-review/stage combo 108 passed; writer 384 passed / 2 skipped; determ 61 passed; review 9 passed; `py_compile stage_promotion.py` passed.
- Subagent `Mill` approved with no HIGH/MEDIUM findings.
- No provider launched; no writing started.
