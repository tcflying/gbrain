# s69-mc-codex post-generation review bridge

Recorded: 2026-06-19 China time
Owner/prefix: `s69-mc-codex-`

Clean writer runners in `G:\codex-project\s69-mc-codex` now require post-generation source-bound review before a successful run can be considered complete.

Evidence:

- Commit: `9f193b45 fix(writer): require post-generation reviews`
- New bridge: `services/writer/octos_writer/post_generation_review.py`
- Wired runners: `services/writer/run_matrix.py`, `services/writer/run_drive.py`, `services/writer/run_chunk.py`
- Sealed facade additions: `octos_determ.review_drama_file`, `octos_determ.render_three_reviews`

Behavior:

- After `final_gate.ok`, official-yika delivery, and `valid_generation_manifest.ok` all pass, runners run drama-format source-bound review, write `review_result.json`, render exactly the required three review markdown files, and attempt `C:\Users\datoo\Desktop\v11\mc-codex` export when V11 is A+ or above.
- Top-level review error blocks the runner.
- Required GLM/MMX/GPT synth degraded review blocks the runner.
- A+ / S / S+ or total-only `total >= 82` requires successful V11 mc-codex export.
- `kimi_shadow`, other shadow files, and Claude outputs do not count as required three-review files.

Verification:

- `python -m pytest services\writer\tests\test_post_generation_review.py services\writer\tests\test_v11_delivery.py -q` -> 13 passed
- `python -m pytest services\writer\tests -q -k "not live"` -> 149 passed, 12 deselected
- `python -m pytest services\determ\tests -q` -> 47 passed
- `py_compile` passed for changed writer/determ files
- Subagent reviews: `Averroes`, `Aristotle`, `Helmholtz`
