# s69-mc-codex-drama-rating-gate-20260619

Owner/prefix: `s69-mc-codex-`
Recorded: 2026-06-19 China time

## Summary

Codex lane `s69-mc-codex` added the clean determ drama/content rating gate and pushed it to the project branch.

## Evidence

- Worktree: `G:\codex-project\s69-mc-codex`
- Branch: `s69-mc-codex`
- Commit: `4f42a50b fix(determ): add drama rating safety gate`
- QA report: `G:\codex-project\s69-mc-codex\docs\qa\drama-rating-safety-gate-20260619.md`

## Behavior

- `drama_rating.scan()` uses packaged `data/drama_rating.json` first and exposes `config_error` on fallback.
- `facade.verify()` and `facade.review_script()` both route hard hits to `b.hard` and review-only hits to `b.nh_determ`.
- Short-drama normal action violence is review-only.
- Severe sexual/drug and `血祭童女`-class child-harm occult content are hard blockers.

## Verification

- `test_drama_rating.py`: 8 passed.
- determ targeted suite: 29 passed.
- writer offline suite: 65 passed, 2 deselected.
- review suite: 9 passed.
- Subagent reviewer `Feynman`: final 0 issues / LGTM.
