# 239-codex-new comet-ecc perfect hard gates

Recorded: 2026-06-18 China time
Owner/prefix: `239-codex-new-`
Marker: `239-codex-new-comet-ecc-perfect-hard-gates-20260618`

## Conclusion

For comet-ecc, "perfect" means measurable hard gates:

- exact token accounting when available;
- scoped naming and collision prevention;
- task dedupe by raw task hash;
- explicit decision gates;
- execute dispatch safety gate.

## Implementation evidence

Repo: `G:\codex-project\comet-ecc`
Branch: `239-codex-new`
Commit: `6002784 feat: add exact tokens global names and decision gates`

Implemented:

1. `auto` token budget prefers `tiktoken:cl100k_base`; output includes `tokenizer` and `exact=true`.
2. `name --scope project|global`; global registry defaults to `~\.comet-ecc\names.json`; tests isolate via `COMET_ECC_GLOBAL_HOME`.
3. `auto --apply` writes `.comet-ecc/tasks.json`; duplicate raw task SHA returns `task_registry.reused=true`.
4. `decide --project <repo>` emits blocking decision codes, including `build_config_required`.
5. `dispatch --execute` is gated and reports `spawned=false` plus `execute_blocked_reason=blocking_decision_or_guard` when blocked.

Verification:

- `python -m py_compile comet_ecc.py` passed.
- `python -m pytest tests\test_adapters.py` passed: 13 passed.
- `python tests\e2e_matrix.py` passed.

Boundary: external live agent spawn, Hermes live dispatch, provider live execution, and real profile mutation remain intentionally gated until profile permission, concurrency limits, stop/rollback behavior, and E2E evidence exist.
