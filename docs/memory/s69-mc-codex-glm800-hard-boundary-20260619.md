# s69-mc-codex GLM 800K review hard boundary

Recorded: 2026-06-19 China time
Owner/prefix: `s69-mc-codex-`

For `G:\codex-project\s69-mc-codex`, GLM review is `GLM-5.2-thinking` direct 800K big-window review. This 800K token boundary is now a hard review-dispatch boundary for every review path that uses the GLM panel, including prose and drama/official-yika review.

Evidence:

- Commit: `3d79c96e fix(review): enforce glm 800k boundary`
- `review_dispatch._BIG_TOK = 800000`
- `est_tokens <= 800000` may enter GLM + MiniMax-M3 panel.
- `est_tokens > 800000` returns `tier=over` before prose or drama panel judges.
- Direct `review_mid.run_mid()` above 800K returns `mid_input_over_800k_tok` without calling judges.
- Tests:
  - `python -m pytest services\determ\tests\test_review_dispatch_legacy.py -q` -> 10 passed
  - `python -m pytest services\determ\tests -q` -> 47 passed
  - `python -m py_compile services\determ\_legacy\tools\qa\review_dispatch.py services\determ\_legacy\tools\qa\review_mid.py`
- Review:
  - `Linnaeus` flagged the drama-scope ambiguity.
  - `Kierkegaard` confirmed closure after adding the drama 800K boundary test.

Operational impact: do not schedule `800001..950000` token texts into the GLM single-window review panel in this lane. Use over/cross-window or another explicitly approved large-window strategy.
