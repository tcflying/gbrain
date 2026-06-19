# s69-mc-codex-route-pressure-test-isolation-20260619

Recorded: 2026-06-19 15:22:36 中国时间
Owner/prefix: `s69-mc-codex-`

## Lesson

Provider wrapper tests that intentionally trigger route-pressure behavior
(`429`, timeout, network/remote disconnect) must isolate route-pressure state
with `OCTOS_PROVIDER_ROUTE_PRESSURE_FILE` pointing to a per-test temporary file.

`services/writer/runs/provider_route_pressure.json` is runtime production state,
not a test scratch file. Offline tests must not create or mutate it, otherwise
the first 40-episode readiness preflight can be falsely blocked by stale test
cooldown evidence.

## Evidence

- Project commit: `92e1d021 test(writer): isolate route pressure state`
- Changed test: `services/writer/tests/test_mmx_client.py`
- Readiness report: `docs/qa/writer-readiness-audit-20260619.md`
- Daily log/todo: `619.md`, `619todo.md`
- Verification:
  - `python -m pytest services\writer\tests\test_mmx_client.py services\writer\tests\test_provider_readiness.py services\writer\tests\test_providers.py -q` -> 30 passed
  - `python -m pytest services\writer\tests -q -k "not live"` -> 115 passed, 7 deselected
  - `python -m pytest services\determ\tests -q` -> 35 passed
  - `python -m pytest services\review\tests -q` -> 9 passed
  - `Test-Path services\writer\runs\provider_route_pressure.json` -> False
- Subagent review: `Copernicus` read-only review, CRITICAL/HIGH/MEDIUM/LOW all 0, APPROVE.

## Current launch boundary

Code preflight gates are closed for valid-generation manifest, provider
quota/route gate, stop/clear evidence, no-Claude review, GLM-5.2 800K review,
and official 一卡 delivery. Live 40-episode writing still requires runtime
inputs: real `OCTOS_BRIEF_FILE`, fresh provider quota proof, route-pressure clear
proof, and selected matrix plan.
