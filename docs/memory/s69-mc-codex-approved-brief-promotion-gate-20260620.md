# s69-mc-codex-approved-brief-promotion-gate-20260620

Recorded: 2026-06-20 China time
Owner/prefix: `s69-mc-codex-`

## Summary

Approved candidate brief promotion in `G:\codex-project\s69-mc-codex` now fails closed when the approved brief body or sidecar manifest cannot be written.

## Evidence

- Project code commit: `6a6a43229 fix(writer): guard approved brief promotion writes`.
- Project log commit: `dbbf0c427 docs: record approved brief promotion gate`.
- Branch pushed: `s69-mc-codex` to `octosgh/s69-mc-codex`.
- CodeGraph sync completed / already up to date.
- Paperclip memory commit: `3be80c8a memory: record s69 mc approved brief gate`.

## Implementation

- `services/writer/octos_writer/brief_promotion.py` records `write_result` on successful approved brief promotion.
- On write failure it returns `ok=false`, `candidate_status=brief_promotion_write_failed`, `approved_for_production=false`, and `reason=brief_promotion_write_failed`.
- If the approved body was already written but the manifest write fails, it attempts to remove the half-written approved brief and records `approved_body_cleanup`.
- If cleanup fails and the approved body remains, the failure manifest status mismatch blocks `run_config` / launch preflight through `candidate_status_mismatch`.
- `services/writer/promote_candidate_brief.py` returns exit code 0 only when manifest `ok=true`; write failures return 2 with structured `reason/write_result/manifest_write_result`.

## Verification

- Candidate/run_config/launch targeted tests = 83 passed.
- CLI approved-path directory-conflict probe returned rc=2 with `reason=brief_promotion_write_failed` and no traceback.
- `python -m pytest services\writer\tests -q` = 346 passed / 2 skipped.
- `python -m pytest services\determ\tests -q` = 61 passed.
- `python -m pytest services\review\tests -q` = 9 passed.
- Related `py_compile` passed.
- Subagent `Ptolemy the 2nd` first found one HIGH around cleanup failure; after fixing failure manifest status and adding a runner-block regression, final review was APPROVE with 0 findings.

## Boundary

- Clean A+ or higher Codex-lane V11 bundles must export to `C:\Users\datoo\Desktop\v11\MC-Codex`, not lowercase `mc-codex`.
- Human-review-required A+ or higher bundles continue to export to `C:\Users\datoo\Desktop\v11\GA-Codex`.
- No live provider writing/review was launched.
- No claim was made that S, 40-episode, or 80-episode goal gates are achieved.
