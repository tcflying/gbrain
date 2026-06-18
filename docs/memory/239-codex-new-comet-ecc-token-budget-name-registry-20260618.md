# 239-codex-new comet-ecc token budget name registry

Recorded: 2026-06-18 China time
Owner/prefix: `239-codex-new-`
Marker: `239-codex-new-comet-ecc-token-budget-name-registry-20260618`

`G:\codex-project\comet-ecc` commit `386f6cd feat: add token budget and name registry` implemented token budget control and duplicate-name prevention.

## Commands

```text
python G:\codex-project\comet-ecc\comet_ecc.py name --namespace change --raw "Fix frontend bug" --reserve --project <repo>
python G:\codex-project\comet-ecc\comet_ecc.py auto --task "<long task>" --max-task-tokens 32 --apply --project <repo>
```

## Evidence

1. Long task input can be compressed under the configured token cap.
2. Compressed text preserves `sha256=...`.
3. Name output avoids full raw long text and uses `raw_excerpt` / `raw_sha256`.
4. `.comet-ecc/names.json` prevents duplicate project-local names and resolves slug collisions with deterministic suffixes.
5. Verification passed: `py_compile`, pytest `10 passed`, and `tests\e2e_matrix.py`.

## Boundary

This is not yet full global intelligence: token count is local estimator, and naming is project-local rather than global cross-repo registry.
