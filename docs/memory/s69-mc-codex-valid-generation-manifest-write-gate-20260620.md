# s69-mc-codex-valid-generation-manifest-write-gate-20260620

Owner/prefix: s69-mc-codex-
Recorded: 2026-06-20 China time

## Durable lesson

In `G:\codex-project\s69-mc-codex`, valid-generation manifest write failures
must be controlled route-gate failures, not writer hard crashes. If the primary
or latest manifest path cannot be written, the writer runner must receive
`manifest.ok=false` so it can write stop-clear evidence and block post-review.

## Evidence

- Project commit: `2d61ffeb4 fix(writer): fail valid manifest write errors closed`
- Branch/push target: `s69-mc-codex` -> `octosgh/s69-mc-codex`
- Code path: `services/writer/octos_writer/generation_manifest.py`
- Test path: `services/writer/tests/test_generation_manifest.py`

## Behavior

- Primary write failure -> `ok=false`, `reason=manifest_write_failed`.
- Latest write failure -> `ok=false`, `reason=latest_manifest_write_failed`, primary manifest rewritten as fail-closed evidence.
- Primary rewrite failure after latest success -> `ok=false`, `reason=manifest_rewrite_failed`, latest rewrite attempted as fail-closed evidence.
- Successful primary/latest manifests now match the returned manifest, including write proof fields.

## Verification

- Generation manifest + promotion targeted tests: `9 passed`
- Full writer tests: `318 passed, 2 skipped`
- Determ tests: `61 passed`
- Review tests: `9 passed`
- Subagent review: Descartes final APPROVE, 0 findings
- CodeGraph sync: already up to date

## Operational impact

This is a route/proof gate repair. It blocks review/export/promotion when the
valid-generation manifest cannot be written, and must not be counted as story
hard collapse or model-quality evidence.
