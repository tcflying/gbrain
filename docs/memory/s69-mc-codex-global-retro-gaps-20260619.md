# s69-mc-codex global retro gaps

Recorded: 2026-06-19 China time
Owner/prefix: `s69-mc-codex-`

Codex re-ran a global retro over project logs, `G:\claude-project\octos-MC\6.18.md`, CodeGraph, and current tests.

New evidence and gaps:

- Current `services/review` baseline: 9 passed.
- Current `services/determ` baseline: 24 passed / 1 failed; failure is still missing `services/determ/_legacy/data/config/drama_script_spec.json`.
- Current `services/writer` offline subset: 19 passed / 1 skipped / 1 deselected.
- Current full `services/writer` baseline is not green because `tests/test_write_gate_live.py::test_write_two_episodes_through_gate` auto-runs live MMX when a key exists and failed with `HTTP Error 422: Unprocessable Entity`.
- `services/writer/octos_writer/mmx_client.py` raises `HTTPError` without reading provider body, so 422 cannot be classified as schema, sensitive, quota, route, or provider-input failure.
- `services/writer/tests/test_write_gate_live.py` should become explicit live opt-in or a separate provider profile; default offline baseline should not burn MMX quota or fail due provider volatility.
- `services/determ/_legacy/tools/qa/review_dispatch.py` has a drama-path bug: `format="drama"` uses undefined `path_or_text` while trying to load sibling `canon.json`; selftest does not cover that path.
- Deep C4 gaps from `6.18.md` remain separate and must not be counted as solved by V11 injection: foreshadow overdue is advisory, relationship/secrets bible persistence still needs a later migration, and `arc_score.py` is not wired into writer pacing self-check.
- `docs/qa/reference-sample-review-20260619.md` shows current format gate mismatches the official `《锦衣羽刃》一卡(1).docx` sample and sees 11 episode titles; renderer/validator work must be target-count parameterized for 40 while treating the official sample as truth, not using current gate failures to reject it.

Operational impact:

- Do not report writer as fully green; say offline writer subset is green but live MMX route currently fails.
- Before production writing, fix/spec-check `drama_script_spec.json`, official format validator, live-provider error evidence, and the drama review path bug.
