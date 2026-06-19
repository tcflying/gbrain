# s69-mc-codex V11 export and GLM 800K review boundary

Recorded: 2026-06-19 China time
Owner/prefix: s69-mc-codex-
Project commit: 6001ab6b fix(writer): gate v11 mc-codex export

Durable facts:
- GLM review in this lane is direct 800K big-window review. `review_small.py` now calls GLM at `est_tokens == 800000`, and `review_dispatch.review()` mid tier calls GLM/MMX for `800000 < tokens <= 950000`.
- V11 A+ export writes to `C:\Users\datoo\Desktop\v11\mc-codex` only when V11 is A+ or above and three reviews exist: MiniMax-M3-think, GLM-5.2-think, GPT-5.5 synth.
- Claude review must not be exported in mc-codex bundle.
- V11 export uses grade first: only `A+`, `S`, `S+` pass. If grade is missing, official V11 A+ fallback threshold is `total >= 82`. `grade=A,total=89` is blocked.
- `review_dispatch.py --v11-json` returns nonzero when V11 export fails; old no-parameter review path remains unchanged.

Verification:
- 17 targeted V11/review tests passed.
- writer offline: 141 passed, 11 deselected.
- determ: 44 passed.
- py_compile passed for changed Python files.
- Subagent James findings fixed; Fermat final review 0 findings / APPROVE.
