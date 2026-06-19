# s69-mc-codex-future-quota-proof-gate-20260620

Owner/prefix: s69-mc-codex-
Recorded: 2026-06-20 China time

## Durable lesson

In `G:\codex-project\s69-mc-codex`, provider quota freshness proof must fail
closed when `checked_at` is far in the future. Future timestamps beyond the
allowed clock skew can otherwise fake a fresh quota proof and unlock provider
writing/review too early.

## Evidence

- Project commit: `e7da6d556 fix(writer): reject future quota proof timestamps`
- Branch/push target: `s69-mc-codex` -> `octosgh/s69-mc-codex`
- Code path: `services/writer/octos_writer/provider_readiness.py`
- Test path: `services/writer/tests/test_provider_readiness.py`
- Block reason: `future_checked_at`
- Default skew tolerance: `300` seconds
- Env override: `OCTOS_PROVIDER_QUOTA_PROOF_FUTURE_SKEW_S`

## Verification

- Provider readiness + launch preflight tests: `62 passed`
- Full writer tests: `316 passed, 2 skipped`
- Determ tests: `61 passed`
- Review tests: `9 passed`
- Subagent review: Pauli APPROVE, 0 findings
- CodeGraph sync: already up to date

## Operational effect

Live provider writing/review gates must not accept quota proof if the proof time
is beyond allowed future clock skew. Minor skew is still allowed to avoid false
failures from clock mismatch.
