# s69-jc-codex reference review path

Recorded: 2026-06-19 16:38 China time
Owner/prefix: `s69-jc-codex-`

Codex lane implementation result:

- Project: `G:\codex-project\s69-jc-codex`
- Commit: `cfa63eb3 fix: add diagnostic reference review path`
- Added/tracked `octos-core/tools/qa/docx_source.py`.
- `drama_review_panel.split_drama_episodes()` now falls back to deterministic clean-DOCX/reference heading split so `第一集`, `第N章 标题`, and `①标题` reference samples do not parse as zero episodes.
- `review_dispatch.py --reference-review` is diagnostic-only for external reference samples. It can bypass `valid_generation_manifest.json` only in that mode and records `review_allowed=false`, `delivery_allowed=false`.
- `--reference-review --md-dir` is blocked to prevent diagnostic reference reviews from generating production-shaped three-review files.
- Production drama file review still requires `valid_generation_manifest.json`.
- GLM review rule reaffirmed for this lane: GLM is also direct 800K big-window review; old 204K GLM downgrade is historical only.

Evidence:

- `docs/qa/s69-jc-codex-reference-sample-split-20260619.md`
- `docs/qa/s69-jc-codex-reference-review-summary-20260619.md`
- `docs/qa/s69-jc-codex-reference-review-path-review-rerun-20260619.md` = APPROVE
- Tests: py_compile, `drama_review_panel.py --selftest`, `review_dispatch.py --selftest`, negative `--reference-review --md-dir`.
- CodeGraph sync returned `Already up to date`.
- Project push blocked by `Permission to 1jehuang/jcode.git denied to tcflying` / GitHub HTTP 403.

Operational rule:

Reference sample reviews are diagnostic-only and cannot be used as A+/S production evidence. Do not commit clean extracted reference full text or raw reference review JSON.
