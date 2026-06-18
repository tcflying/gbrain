# s69-mc-codex Claude session deep retro

Recorded: 2026-06-19 China time
Owner/prefix: `s69-mc-codex-`

Codex parsed the full Claude session JSONL:
`C:\Users\datoo\.claude\projects\G--claude-project-multica\c5350ae2-3a45-4a62-8132-866477e1e160.jsonl`.

Session size inspected: 6632 JSONL lines.

Keyword bucket counts:

- format/Yika: 674
- matrix/40: 361
- review: 5458
- todo/gap: 583
- provider: 1658
- safety/C4: 392
- commit/push: 2084
- user correction: 759

Additional findings recorded for `s69-mc-codex`:

- Claude session line 4077 recorded old Claude-lane correction `M3最大并发=4`; current Codex lane is superseded by the user's later rule: MMX=6, GLM=2, Codex=2.
- Claude session line 4096 says `craft_library`, `script_blueprints`, and `dynamics_library_v2` are S+ gold. Current Codex copy has `octos_corpus/craft.py` reading the main MMX root and outline/episode inject blueprints/craft, but `OCTOS_FEWSHOT` default still points to `G:\claude-project\网文\octos\data\config\hongguo_fewshot.json`. Production needs local/env proof plus prompt injection evidence.
- Claude session lines 4054/4055 record the S+ boundary: deterministic/heuristic scoring tops out around A+ 84.5; S+ cannot be proven by determ alone and needs whole-card V11/D panel/three-review plus craft evidence.
- Current `services/writer/run_matrix.py` only calls `octos_review.v11.score_v11()` after concatenating output. It does not first call `octos_determ.review_script()`. Since per-episode `verify()` skips cross-episode `missing_episode` and `multi_version`, a matrix final claim needs a whole-script determ gate.
- Current `services/writer/octos_writer/outline.py` retries exact-N, but if all tries under-produce it returns the best undercount. `run_matrix.py` can still score that partial output; production runner needs an exact-count refusal gate.
- Claude session final lessons stress liveness monitoring: stalls may not produce completion/failure events. A 40-episode run needs checkpoint mtime or heartbeat monitoring in addition to per-episode watchdogs.

Operational impact:

- Do not start a full writing run before fixing or explicitly gating: provider error body/classification, live-test opt-in, drama review path bug, exact episode count, whole-script determ, official-format validator, and liveness monitoring.
