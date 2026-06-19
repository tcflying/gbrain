# s69-mc-codex MMX-only matrix entry gate

Recorded: 2026-06-20 05:28 China time
Owner/prefix: s69-mc-codex-
Project: `G:\codex-project\s69-mc-codex`
Branch: `s69-mc-codex`
Commit: `c2407b01e fix(writer): enforce mmx-only matrix entry`

## What changed

Codex closed a live-entry bypass in the MC-Codex writer lane.

Current writing matrix:
- `m3@disabled:0.1`
- `m3@disabled:1.0`
- `m3@disabled:1.9`
- `m3@adaptive:0.1`
- `m3@adaptive:1.0`
- `m3@adaptive:1.9`

Implementation:
- `matrix._default_plan()` now defaults to MMX-M3 six lanes instead of the old mixed M3/GLM/Codex writer plan.
- `matrix.mmx_six_lane_violations()` is shared by `launch_preflight` and `run_matrix.py`.
- `run_matrix.py` checks matrix policy before provider readiness and provider launch.
- Illegal plans write `matrix_plan_policy_failed.json` plus stop-clear evidence and return 2.

## Boundary

This does not remove GLM/Codex support for review, diagnostics, or explicitly authorized future non-writing work. It only closes the current writing-provider route.

## Verification

- Writer tests: `314 passed, 2 skipped`.
- Determ tests: `61 passed`.
- Review tests: `9 passed`.
- Targeted matrix/launch/provider tests: `70 passed`.
- Subagent review: `James` APPROVE, 0 findings.
- CodeGraph: `codegraph sync` completed / already up to date.

No live provider writing was started. No 40/80 S completion claim was made.
