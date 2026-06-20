# s69-mc-codex-brief-manifest-provenance-gate-20260620

Recorded: 2026-06-20 China time
Owner/prefix: `s69-mc-codex-`

## Summary

Production brief provenance in `G:\codex-project\s69-mc-codex` now rejects explicit failed brief sidecar manifests.

## Evidence

- Project code commit: `9b04fcf8c fix(writer): reject failed brief manifests`.
- Project log commit: `bcc57fdad docs: record brief manifest provenance gate`.
- Branch pushed: `s69-mc-codex` to `octosgh/s69-mc-codex`.
- CodeGraph sync completed / already up to date.
- Paperclip memory commit: `6d46c812 memory: record s69 mc brief provenance gate`.

## Implementation

- `brief_provenance.evaluate_brief_provenance()` adds `brief_manifest_not_ok` when manifest `ok` is explicitly `false`.
- When the brief text approval status is `approved_for_production`, manifest `approved_for_production=false` adds `brief_manifest_not_approved_for_production`.
- Old legal approved manifests that do not carry these fields remain compatible.
- Candidate-only promotion input is not blocked by the new `approved_for_production=false` check because the text status is `candidate_only`.

## Verification

- run_config/launch/candidate targeted tests = 85 passed.
- `python -m pytest services\writer\tests -q` = 348 passed / 2 skipped.
- `python -m pytest services\determ\tests -q` = 61 passed.
- `python -m pytest services\review\tests -q` = 9 passed.
- Related `py_compile` passed.
- Subagent `Carson the 2nd` reviewed the batch read-only and approved with 0 findings.

## Boundary

- No live provider writing/review was launched.
- No claim was made that S, 40-episode, or 80-episode goal gates are achieved.
