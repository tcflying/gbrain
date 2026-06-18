# s69-mc-codex-provider-wrapper-hardening-20260619

Recorded: 2026-06-19 05:38:59 中国时间
Owner/prefix: `s69-mc-codex-`

## Durable fact

The clean writer provider wrappers in `G:\codex-project\s69-mc-codex` were
hardened before live writing:

1. MMX/MiniMax-M3 and GLM now preserve HTTP status, reason, provider code,
   provider message, and response body tail on final HTTP failure.
2. Retryable HTTP `429/5xx` still uses backoff and was covered with
   retry-then-success tests for both MMX and GLM.
3. Codex writer now treats any non-zero `codex exec` return code as failure
   even if stdout contains text; stderr/stdout tails are retained for evidence.
4. Codex output cleaner removes known hook metadata only and preserves story
   lines beginning with `hook:`.
5. No live provider writing was launched in this batch.

## Evidence

- Project commit: `610c4842 fix(writer): preserve provider failure evidence`
- Branch/push target: `s69-mc-codex` on `octosgh`
- QA report: `G:\codex-project\s69-mc-codex\docs\qa\provider-wrapper-hardening-20260619.md`
- Tests:
  - `python -m pytest services\writer\tests\test_mmx_client.py services\writer\tests\test_providers.py -q` -> 9 passed
  - `python -m pytest services\writer\tests -q -k "not live"` -> 31 passed, 2 deselected
  - `python -m py_compile services\writer\octos_writer\provider_errors.py services\writer\octos_writer\mmx_client.py services\writer\octos_writer\providers.py services\writer\tests\test_mmx_client.py services\writer\tests\test_providers.py` -> passed
- Subagent review: `Parfit` first pass found two LOW issues; both fixed and second pass confirmed closed.

## Operational impact

Provider route/schema/quota errors should no longer be flattened into opaque
`HTTP Error 422` style strings or mistaken for successful story prose. This
reduces the risk of classifying provider failures as story hard collapse or
feeding failed provider stdout into the writing matrix.

## Remaining follow-ups

- Add Codex JSON event parsing if Codex is used in live writing matrix.
- Add explicit proxy policy contract tests.
- Make timeout classification machine-readable.
