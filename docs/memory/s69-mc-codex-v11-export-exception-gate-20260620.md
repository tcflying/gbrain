# s69-mc-codex-v11-export-exception-gate-20260620

Owner/prefix: s69-mc-codex-
Recorded: 2026-06-20 China time

## Durable lesson

In `G:\codex-project\s69-mc-codex`, V11 export exceptions inside
post-generation review must fail closed and persist evidence. They must not
hard-crash the writer runner before `post_generation_review_manifest.json` and
run-level stop-clear evidence are written.

## Evidence

- Project commit: `89f227362 fix(writer): fail v11 export exceptions closed`
- Branch/push target: `s69-mc-codex` -> `octosgh/s69-mc-codex`
- Code paths:
  - `services/writer/octos_writer/post_generation_review.py`
  - `services/writer/run_matrix.py`
- Tests:
  - `services/writer/tests/test_post_generation_review.py`
  - `services/writer/tests/test_run_matrix_promotion.py`

## Behavior

- `v11_export_func(...)` exception -> `ok=false`, `reason=v11_export_exception`, `written=[]`, persisted manifest.
- `run_matrix` no longer lets `gate.reason=ok` mask post-review failure.
- Post-review failure now writes stop-clear reason `post_generation_review_failed`.

## Verification

- Post-review + run-matrix targeted tests: `32 passed`
- Full writer tests: `320 passed, 2 skipped`
- Determ tests: `61 passed`
- Review tests: `9 passed`
- Subagent review: Mendel final APPROVE, 0 findings
- CodeGraph sync: already up to date

## Operational impact

V11 export filesystem/runtime errors are route/proof gate failures. They block
review/export/promotion and must not be reported as source-bound story hard
collapse or model quality failure.
