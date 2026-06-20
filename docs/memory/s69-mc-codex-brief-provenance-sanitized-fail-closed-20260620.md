# s69-mc-codex brief provenance sanitized fail-closed

Owner/prefix: `s69-mc-codex-`
Recorded: 2026-06-20 21:19 +0800 China time

- Project: `G:\codex-project\s69-mc-codex`
- Branch/remote: `s69-mc-codex` -> `octosgh/s69-mc-codex`
- Commit: `901490de5 fix(writer): reject sanitized brief provenance`

Codex found and fixed a proof-chain gap: sanitized candidate brief manifests could be written with `serialization_sanitized=True`, but `brief_provenance.evaluate_brief_provenance()` did not reject that flag before candidate promotion.

Current rule:

- Reject top-level `serialization_sanitized`.
- Reject `write_result.serialization_sanitized`.
- Reject `manifest_write_result.serialization_sanitized`.
- Keep outer failure reason as `brief_provenance_invalid` so promotion, runner config, and launch preflight all fail closed through the existing path.

Verification:

- candidate brief tests: 18 passed
- writer offline tests: 366 passed
- determ tests: 61 passed
- review tests: 9 passed
- `py_compile brief_provenance.py`: passed
- CodeGraph sync: completed / already up to date

Subagent review:

- `Wegener` / gpt-5.5 read-only review first found one LOW for missing nested sanitized write-result coverage.
- The LOW was fixed with `test_brief_provenance_rejects_nested_sanitized_write_results`.
- Final review: CRITICAL/HIGH/MEDIUM/LOW all 0, LGTM.

No live provider writing was started.
