# s69-jc-codex GLM 800K review routing and patch rehydrate

Recorded: 2026-06-19 15:10:24 中国时间
Owner/prefix: `s69-jc-codex-`

## Durable correction

GLM review is now direct 800K big-window for this lane. Old GLM 204K/small-window assumptions and Claude review fallbacks are not valid for current `s69-jc-codex` review routing.

## Evidence

- Worktree: `G:\codex-project\s69-jc-codex`
- Commits: `56cf99a4 fix: enforce glm 800k review routing`; `384eafb2 docs: record glm 800k routing pass`
- Runtime files fixed: `review_mid.py`, `review_small.py`, `review_dispatch.py`, `review_xwin.py`, `cross_window_judge.py`
- Patcher fixed: `octos-jc\patches\apply_review_4tier.py`; new GLM800K diffs include `review_mid`, `review_small`, `review_dispatch`, `review_xwin`
- Rehydrate now checks 12 files and returned `ok=true`, `patch_count=12`, `errors=[]`
- Independent review final artifact: `docs/qa/s69-jc-codex-glm800k-review-final-rerun-20260619.md`, result `APPROVE`
- Passed selftests: review_mid, review_small, review_dispatch, review_xwin, cross_window_judge, drama_review_panel, drama_pipeline
- CodeGraph sync returned `Already up to date`
- Project push to `origin/s69-jc-codex` remains blocked by GitHub 403 for `tcflying`

## Operational impact

Future s69-jc-codex review work should assume GLM+MMX panel, GPT/Codex synthesis, no live Claude reviewer unless explicitly re-authorized. For over-800K review, xwin must keep MAP windows at 800K token equivalent so GLM stays active.
