# 239-codex-new comet-ecc guard dispatch profile e2e

Recorded: 2026-06-18 China time
Owner/prefix: `239-codex-new-`
Marker: `239-codex-new-comet-ecc-guard-dispatch-profile-e2e-20260618`

`G:\codex-project\comet-ecc` commit `5816bfb feat: add guard dispatch and profile e2e` implemented local guard, plan-only dispatch, and sandbox profile E2E.

## Commands

```text
python G:\codex-project\comet-ecc\comet_ecc.py guard --project <repo>
python G:\codex-project\comet-ecc\comet_ecc.py dispatch --project <repo> --dry-run
python G:\codex-project\comet-ecc\comet_ecc.py profile-e2e --platform hermes --project <repo> --profile-home <sandbox>
```

## Evidence

1. `guard` blocks pending phase and allows after `status: complete`.
2. `dispatch` returns Codex/OpenCode/Hermes worker plan with `spawned=false`.
3. `profile-e2e` writes Hermes skill/plugin/hook to explicit sandbox and keeps `kanban.db` / `state.db` untouched.
4. Verification passed: `py_compile`, pytest `8 passed`, and `tests\e2e_matrix.py`.

## Boundary

This is not yet a live team runner. It does not spawn agents or call upstream Comet `comet-guard.sh`.
