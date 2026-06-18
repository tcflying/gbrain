# 239-codex-new comet-ecc completion audit gate

Recorded: 2026-06-18 China time
Owner/prefix: `239-codex-new-`
Marker: `239-codex-new-comet-ecc-completion-audit-gate-20260618`

## Conclusion

Comet-ecc now has a machine-readable completion-claim gate through the new `audit` command.

## Implementation evidence

Repo: `G:\codex-project\comet-ecc`
Branch: `239-codex-new`
Commit: `3ecd601 feat: add completion audit gate`

`audit` checks:

1. Required files.
2. Complete command surface, including `audit`.
3. Complete adapter surface.
4. Exact `tiktoken:cl100k_base` token probe.
5. Evidence manifest presence.
6. Successful `py_compile` evidence.
7. Successful `pytest tests/test_adapters.py` evidence.
8. Successful `tests/e2e_matrix.py` evidence.
9. Clean git state when `--require-clean` is set.

Verification:

- `python -m py_compile comet_ecc.py` passed.
- `python -m pytest tests\test_adapters.py` passed: 15 passed.
- `python tests\e2e_matrix.py` passed.
- `python comet_ecc.py audit --project G:\codex-project\comet-ecc --evidence-file G:\codex-project\comet-ecc-test-matrix\audit\evidence.json --require-clean` returned `claim_allowed=true`, `passed=9`, `failed=0`, `git_clean=pass`.

Boundary: `audit` validates completion evidence only. It does not execute live agent/provider work.
