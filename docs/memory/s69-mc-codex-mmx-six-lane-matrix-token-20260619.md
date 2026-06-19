# s69-mc-codex-mmx-six-lane-matrix-token-20260619

Recorded: 2026-06-19 15:31:38 中国时间
Owner/prefix: `s69-mc-codex-`

## Lesson

The current s69-mc-codex first writing matrix can express the MiniMax/MMX
six-lane plan explicitly with combo tokens:

`m3@disabled:0.1,m3@disabled:1.0,m3@disabled:1.9,m3@adaptive:0.1,m3@adaptive:1.0,m3@adaptive:1.9`

This maps to `thinking=disabled/adaptive` times temperatures `0.1/1.0/1.9`.
Legacy matrix tokens remain valid, including `m3@0.9`, `m3@adaptive`,
`glm@think`, `glm@greedy`, and `codex@high`.

## Evidence

- Project commit: `a9bba10c fix(writer): support mmx six-lane matrix tokens`
- Files: `services/writer/octos_writer/matrix.py`, `services/writer/tests/test_matrix_safety.py`
- Verification:
  - `python -m pytest services\writer\tests\test_matrix_safety.py services\writer\tests\test_provider_readiness.py -q` -> 14 passed
  - `python -m pytest services\writer\tests -q -k "not live"` -> 116 passed, 7 deselected
  - `python -m pytest services\determ\tests -q` -> 35 passed
  - `python -m pytest services\review\tests -q` -> 9 passed
  - changed files `py_compile` passed
- Subagent review: `Ohm` read-only review, CRITICAL/HIGH/MEDIUM/LOW all 0, APPROVE.

## Launch boundary

The default mixed matrix was intentionally not changed. For MMX-only first 40,
set `OCTOS_MATRIX_PLAN` to the six-lane string above so required providers are
only `m3`. A real `OCTOS_BRIEF_FILE` is still required before live 40-episode
writing; the default runner brief remains a test brief.
