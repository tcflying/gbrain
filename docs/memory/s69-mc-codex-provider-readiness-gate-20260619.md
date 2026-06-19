# s69-mc-codex provider readiness gate

Recorded: 2026-06-19 China time
Owner/prefix: `s69-mc-codex-`

Project commit:
- Repo/worktree: `G:\codex-project\s69-mc-codex`
- Branch/remote: `s69-mc-codex` -> `octosgh/s69-mc-codex`
- Commit: `257bd29d fix(writer): gate provider readiness before production runs`

Operational rule:
- Clean writer 40+ production runs must prove provider quota/remains freshness and route-pressure cooldown state before any writer provider call starts.

Implementation:
- Added `services/writer/octos_writer/provider_readiness.py`.
- `run_matrix.py` gates providers from the actual `OCTOS_MATRIX_PLAN`.
- `run_drive.py` gates `m3`.
- `run_chunk.py` gates the selected provider.
- Quota proof source is `provider_quota_proof.json` or `OCTOS_PROVIDER_QUOTA_PROOF_FILE`.
- Quota proof freshness defaults to 900 seconds via `OCTOS_PROVIDER_QUOTA_PROOF_TTL_S`.
- Route pressure source is `provider_route_pressure.json` or `OCTOS_PROVIDER_ROUTE_PRESSURE_FILE`.
- HTTP 429, timeout, route/network disconnect, and structured rate-limit `error_code` variants write cooldown state for later preflight blocking.
- Provider aliasing is shared between preflight and `write_one()`, including `mmx/minimax -> m3`.

Verification:
- Provider targeted tests: 25 passed.
- Writer offline suite: 109 passed, 7 deselected.
- Determ suite: 35 passed.
- Review suite: 9 passed.
- Subagent `Dewey` final review: 0 issues / LGTM.

Remaining blocker:
- Hard-collapse all-stop / clear planned queue evidence package remains required before the first 40-episode production writing run.
