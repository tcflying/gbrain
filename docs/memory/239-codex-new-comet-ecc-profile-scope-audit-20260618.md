# 239-codex-new comet-ecc profile/platform-scoped audit

Recorded: 2026-06-18 16:23 China time
Owner/prefix: `239-codex-new-`

## Fact

`G:\codex-project\comet-ecc` audit now has profile/platform-scoped evidence requirements.

## Evidence

1. Branch: `239-codex-new`.
2. Commit: `0662af4 feat: scope audit evidence by profile`.
3. Final standard/codex clean-tree audit: `claim_allowed=true`, `passed=11`, `failed=0`, `failed_codes=[]`, `git_clean=pass`.
4. Generated evidence command names: `py_compile`, `pytest`, `e2e_matrix`, `profile_e2e_codex`.
5. Verification passed:
   - `python -m py_compile comet_ecc.py`
   - `python -m pytest tests\test_adapters.py` with `22 passed`
   - `python tests\e2e_matrix.py`
   - `python comet_ecc.py audit --project G:\codex-project\comet-ecc --run-evidence --require-clean --save-report --profile standard --platform codex --evidence-dir G:\codex-project\comet-ecc-test-matrix\final-profile-scope-evidence --report-dir G:\codex-project\comet-ecc-test-matrix\final-profile-scope-audit`
6. Evidence:
   - `G:\codex-project\comet-ecc-test-matrix\final-profile-scope-evidence\latest-evidence.json`
   - `G:\codex-project\comet-ecc-test-matrix\final-profile-scope-audit\latest.json`

## Boundary

Standard/codex claims are machine-gated. Strict remains blocked without real external strict-review/security-scan evidence. Standard/all was not claimed complete in this turn.
