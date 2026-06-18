# 239-codex-new comet-ecc audit run evidence

Recorded: 2026-06-18 China time
Owner/prefix: `239-codex-new-`
Marker: `239-codex-new-comet-ecc-audit-run-evidence-20260618`

## Conclusion

Comet-ecc `audit` can now generate its own evidence manifest before auditing.

## Implementation evidence

Repo: `G:\codex-project\comet-ecc`
Branch: `239-codex-new`
Commit: `9a5f7c1 feat: generate audit evidence`

New flags:

- `audit --run-evidence`
- `audit --evidence-dir <dir>`
- `audit --evidence-timeout <seconds>`

Verification:

- `python -m py_compile comet_ecc.py` passed.
- `python -m pytest tests\test_adapters.py` passed: 17 passed.
- `python tests\e2e_matrix.py` passed.
- Final audit with `--run-evidence --require-clean --save-report` returned `claim_allowed=true`, `passed=9`, `failed=0`, `git_clean=pass`, and saved both generated evidence and audit report.

Boundary: generated evidence currently covers three core checks. Future profile-specific suites can add strict profile E2E, security scan, platform doctor, or real profile checks.
