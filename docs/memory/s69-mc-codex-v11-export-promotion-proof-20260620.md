# s69-mc-codex V11 export promotion proof binding

Recorded: 2026-06-20 05:17 China time
Owner/prefix: s69-mc-codex-
Project: `G:\codex-project\s69-mc-codex`
Branch: `s69-mc-codex`
Commit: `fabd1fa33 fix(writer): bind v11 export promotion proof`

## What changed

Codex closed stale V11 A+/S export proof bypasses in the MC-Codex writing lane.

`stage_promotion` now:
- compares `human_review_required`, `v11_export_human_review_required`, `v11_export_out_dir`, `v11_export_source`, and `v11_export` between inline `post_generation_review` and `post_generation_review_manifest.json`;
- requires V11 export proof to have `v11_export.ok=true`, exactly four unique non-empty files, and all files under the declared `out_dir`;
- enforces clean exports under `MC-Codex` and human-review exports under `GA-Codex`;
- derives human-review routing from authoritative `v11.human_review_required` and `v11.uncertain_hard_breaks` as well as post-review/export flags;
- requires the one-script-three-review filename markers `完整剧本`, `评审①-MiniMax-M3-think`, `评审②-GLM-5.2-think`, `评审③-GPT-5.5综合`;
- rejects `Claude`, `Kimi`, `shadow`, and `评审④` export filenames at promotion proof time;
- keeps `run_json` proof bound to the current run path and checks `post_review.run_json_path` / `post_review.script_path` against current intended outputs.

## Verification

- Writer tests: `312 passed, 2 skipped`.
- Determ tests: `61 passed`.
- Review tests: `9 passed`.
- Ohm targeted combo: `94 passed`.
- Subagent review: `Ohm` final APPROVE, 0 findings.
- CodeGraph: `codegraph sync` completed / already up to date.

## Boundary

No live provider writing was started. No 40/80 S completion claim was made.
