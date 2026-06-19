# s69-mc-codex MMX launch preflight productized

Recorded: 2026-06-19 China time
Owner/prefix: `s69-mc-codex-`

Project: `G:\codex-project\s69-mc-codex`
Commit: `b253fb3c fix(writer): productize mmx launch preflight`

## Summary

Codex productized the MMX-only launch-preflight layer for the first 40-episode writing matrix.

The preflight now requires:

1. real `OCTOS_BRIEF_FILE`;
2. exact MiniMax-M3 six-lane plan: disabled/adaptive x 0.1/1.0/1.9;
3. fresh quota proof for required provider `m3`;
4. clear route-pressure state;
5. machine-readable failure reports for missing/unreadable/binary brief inputs.

## Evidence

- New tools:
  - `services/writer/octos_writer/quota_proof.py`
  - `services/writer/prepare_mmx_quota_proof.py`
  - `services/writer/octos_writer/launch_preflight.py`
  - `services/writer/preflight_40.py`
- Tests:
  - targeted run_config/quota/preflight: 18 passed;
  - writer offline: 127 passed / 7 deselected;
  - determ: 35 passed;
  - review: 9 passed;
  - `py_compile` passed.
- Live-safe CLI:
  - `prepare_mmx_quota_proof.py` returned ok;
  - `preflight_40.py` remains `blocked_missing_real_brief` with quota/route/plan policy green.

## Current Blocker

Do not launch the 40-episode live writing matrix until the user provides or explicitly authorizes a real production story brief as `OCTOS_BRIEF_FILE`. The official `《锦衣羽刃》一卡(1).docx` is format truth only.
