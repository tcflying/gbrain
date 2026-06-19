# s69-mc-codex preflight failure write gate and MC-Codex directory correction

Recorded: 2026-06-20 China time
Owner/prefix: s69-mc-codex-

## Durable corrections

- Clean A+ and above Codex-lane V11 bundles must export to `C:\Users\datoo\Desktop\v11\MC-Codex`.
- Do not use lowercase `mc-codex` for the clean A+ directory in current rules, help text, or future deliverables.
- Pending-human-review A+ and above bundles still export to `C:\Users\datoo\Desktop\v11\GA-Codex`.
- This is project-scoped for `G:\codex-project\s69-mc-codex`; do not move it into global AGENTS unless the user explicitly asks for a global rule.

## Implementation result

- Project commit: `39e38eafe fix(writer): guard preflight failure writes` on branch `s69-mc-codex`, pushed to `octosgh/s69-mc-codex`.
- `services/writer/octos_writer/run_config.py` now records `write_result.ok=true/write_path` when `run_preflight_failed.json` writes succeed.
- If the preflight failure manifest cannot be written, `write_preflight_failure()` no longer hard-crashes. It preserves the original preflight `reason` and adds `write_result.reason=preflight_failure_write_failed`, `write_path`, and `write_error`.
- `public_config()` still removes full `brief`; regression tests assert failed manifests do not contain the original secret/default brief text.
- Legacy `review_dispatch.py` help text now says clean A+ exports use `MC-Codex` and pending-human-review exports use `GA-Codex`; no Claude reviewer was restored.

## Verification

- `python -m pytest services\writer\tests\test_run_config.py -q` = 24 passed.
- Runner/preflight/stop-clear combination = 87 passed.
- `python -m pytest services\writer\tests -q` = 338 passed / 2 skipped.
- `python -m pytest services\determ\tests -q` = 61 passed.
- `python -m pytest services\review\tests -q` = 9 passed.
- Related `py_compile` passed; `git diff --check` only reported CRLF warnings.
- Subagent `Fermat` reviewed the batch read-only; two LOW findings were fixed, no CRITICAL/HIGH/MEDIUM remained.

## Boundary

- No live provider writing/review was launched.
- No claim was made that S, 40-episode, or 80-episode goal gates are achieved.
