# 239-codex-new comet-ecc persistent audit reports

Recorded: 2026-06-18 China time
Owner/prefix: `239-codex-new-`
Marker: `239-codex-new-comet-ecc-persistent-audit-reports-20260618`

## Conclusion

Comet-ecc `audit` now supports persistent state evidence reports.

## Implementation evidence

Repo: `G:\codex-project\comet-ecc`
Branch: `239-codex-new`
Commit: `6140821 feat: persist audit reports`

New flags:

- `audit --save-report`
- `audit --report-dir <dir>`

Behavior:

1. Default directory: `<project>\.comet-ecc\audit`.
2. Writes `latest.json`.
3. Writes timestamped history JSON.
4. Includes claim result, requirement list, git head/status, dirty lines, report hash, history path, and latest path.

Verification:

- `python -m py_compile comet_ecc.py` passed.
- `python -m pytest tests\test_adapters.py` passed: 16 passed.
- `python tests\e2e_matrix.py` passed.
- Final audit with sandbox report dir returned `claim_allowed=true`, `passed=9`, `failed=0`, `git_clean=pass`, and saved both latest and history reports.

Boundary: persisted audit reports do not auto-run verification commands. Future improvement can add `verify` or `audit --run-evidence`.
