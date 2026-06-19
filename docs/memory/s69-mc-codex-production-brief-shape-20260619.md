# s69-mc-codex production brief shape gate

Recorded: 2026-06-19 China time
Owner/prefix: `s69-mc-codex-`

Project commit: `2f335e9e fix(writer): validate production brief shape`

Codex added production brief shape validation for writer launch readiness.

Rules:

1. Production-threshold runs require a structured story brief, not only a readable external file.
2. Short shells like `official brief` fail as `brief_shape_invalid`.
3. `OCTOS_PRODUCTION_EPISODE_THRESHOLD` is shared by run config, launch preflight, and brief shape validation.
4. Invalid threshold blocks preflight as `blocked_invalid_production_threshold`.

Evidence:

- targeted tests: 57 passed;
- writer offline: 135 passed / 7 deselected;
- determ: 35 passed;
- review: 9 passed;
- py_compile passed;
- final Parfit review: 0 findings.

Current blocker: real structured production story brief is still required before any 40-episode live matrix.
