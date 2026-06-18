# s69-mc-codex writer matrix and review flow

Recorded: 2026-06-19 China time
Owner/prefix: `s69-mc-codex-`

Project: `G:\codex-project\s69-mc-codex`

Source pass:

- `G:\claude-project\octos-MC\6.18.md`
- Claude session `C:\Users\datoo\.claude\projects\G--claude-project-multica\c5350ae2-3a45-4a62-8132-866477e1e160.jsonl`
- CodeGraph over writer/review/determ nodes in the Codex worktree

Current writer matrix:

- Provider-variant matrix is per-episode best-of-N:
  `m3@0.1,m3@0.5,m3@0.9,m3@1.9,m3@adaptive,glm@think,glm@nothink,glm@greedy,codex@low,codex@high`.
- Caps: M3/MMX 6, GLM 2, Codex 2.
- Per-episode chain: craft/V11/canon/prev_tail prompt -> parallel providers -> determ `verify()` -> repair if no ready -> D 7-dim soft grade -> best candidate -> checkpoint.
- `run_chunk.py` is the separate run-size dimension (`1,10,20,40`) with constant provider and whole-card V11 comparison.
- `drive.py/run_drive.py` is M3-only write/gate/repair validation.

Review and goal rules:

- B/determ is binding for `ready`.
- D 7-dim panel is advisory and used only for ranking/selection.
- V11 is whole-card final verdict; per-episode 7-dim S+ is not whole-card S+.
- Current Codex-lane review export must be MiniMax-M3, GLM-5.2, and GPT-5.5 synth only; no Claude reviewer.

Phase boundary:

- Claude tree checkpoint saved 6/40 ready episodes, but no full 40-episode run and no whole-card V11 verdict were achieved.
- Current Codex copy has no `services/writer/runs`, so ep7 resume is not valid in this lane until ckpt import is explicitly chosen.
- `run_matrix.py` / `run_chunk.py` still use the hardcoded urban-revenge test brief, not the official Jinyi/Yika delivery brief.
- Next flow: fix missing spec / official format validator -> run baselines -> decide ckpt import or fresh start -> canary -> full 40 -> V11 final -> only then build chunk-repair/V11 lift from real needs_fix profile.
