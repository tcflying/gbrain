# s69-mc-codex approved brief manifest sanitized fail-closed

Recorded: 2026-06-20 21:02 +0800
Owner/prefix: `s69-mc-codex-`

- Repo/branch: `G:\codex-project\s69-mc-codex` / `s69-mc-codex`.
- Code commit: `88ef95d81 fix(writer): reject sanitized approved brief manifests`.
- `brief_promotion.promote_candidate_brief()` now treats `serialization_sanitized` while writing the approved manifest as a promotion failure.
- If this happens, the already written approved brief body is cleaned up and the manifest is written as `ok=false`, `candidate_status=brief_promotion_write_failed`, `approved_for_production=false`.
- This prevents a sanitized approved manifest from being accepted as a production `OCTOS_BRIEF_FILE` provenance proof.
- Tests: `test_candidate_brief.py` 16 passed; writer 389 passed / 2 skipped; determ 61 passed; review 9 passed; `py_compile brief_promotion.py` passed.
- Subagent `Boyle` approved with no findings.
- No provider launched; no writing started.
