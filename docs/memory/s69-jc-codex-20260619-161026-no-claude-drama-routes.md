# s69-jc-codex no-Claude drama route hardening

Recorded: 2026-06-19 16:10 China time
Owner/prefix: `s69-jc-codex-`
Project: `G:\codex-project\s69-jc-codex`

## Durable result

- GLM review routing is direct 800K big-window in the current Codex lane.
- `drama_pipeline.py` has no reachable production C-render call to `scene_event_emit` or old `claude-opus-4-8:low`.
- `OCTOS_C_RENDER=1` is request-only evidence and writes `c_render=false`, `c_render_requested=true`, `c_render_executed=false`.
- `drama_pipeline.run_pipeline` / CLI and `script_drama_writer` CLI / standalone / episode writer reject `claude...` writer specs.
- `_write_claude` branches were removed from current production files `drama_pipeline.py` and `script_drama_writer.py`.

## Evidence

- Commit: `949b5dc7 fix: disable stale claude drama routes`.
- Final independent review: `G:\codex-project\s69-jc-codex\docs\qa\s69-jc-codex-c-render-doc-sweep-review-rerun2-20260619.md`.
- Verification: py_compile, selftests, no-Claude route assertion, fixed-string scans, CodeGraph sync.

## Operational impact

- Do not use Claude/Opus reviewer, final audit, or writer route for new Codex Jinyi/Yika production unless the user explicitly re-authorizes and code is reworked.
- Old C-render code is historical/non-production. Re-enabling requires non-Claude resource-bound implementation plus review.
- Project GitHub push is still blocked by 403 for user `tcflying`.
