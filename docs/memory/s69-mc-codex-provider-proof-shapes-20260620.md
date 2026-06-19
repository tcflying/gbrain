# s69-mc-codex provider proof shape gate

Recorded: 2026-06-20 01:33 China time
Owner/prefix: `s69-mc-codex-`

Project/worktree: `G:\codex-project\s69-mc-codex`
Branch: `s69-mc-codex`
Commit: `9aa6296c fix(writer): validate provider proof shapes`

## Lesson

Provider readiness proof files must fail closed on wrong JSON shape. A parseable JSON array/string, or a `providers` field with null/list/string value, is invalid proof and must not be treated as missing/empty but safe.

## Behavior

- Route pressure top-level non-object: `invalid_route_pressure_shape:<type>`.
- Quota proof top-level non-object: `invalid_quota_proof_shape:<type>`.
- `providers` present but non-object: `invalid_*_shape:providers_<type>`.
- Legacy top-level provider-key object remains supported only when `providers` is absent.

## Evidence

- Code: `services/writer/octos_writer/provider_readiness.py`
- Tests: `services/writer/tests/test_provider_readiness.py`
- Verification: provider_readiness `17 passed`; writer full `264 passed, 2 skipped`; determ `56 passed`; review `9 passed`.
- Subagents: `Beauvoir` found the `providers:null` fallback bug; `Hume` approved the fix with 0 findings.

No live provider was started and no production/S/40/80 quality claim was made.
