# 239-codex-new comet-ecc full lifecycle

Recorded: 2026-06-18 China time

Fact:

- comet-ecc now has a complete local lifecycle MVP through `auto --apply`.
- Commit: `868925a feat: add full auto lifecycle`

Lifecycle:

- `.comet-ecc/state.json`
- `.comet-ecc/<phase>.md`
- `open -> design -> build -> verify -> archive`
- Standalone `status: complete` in a phase artifact advances the next run.
- History persists in state JSON.

Evidence:

- `python -m py_compile G:\codex-project\comet-ecc\comet_ecc.py`
- `python -m pytest G:\codex-project\comet-ecc\tests\test_adapters.py` -> 5 passed
- `python G:\codex-project\comet-ecc\tests\e2e_matrix.py` -> passed

Boundary:

- Upstream Comet guard and subagent/team orchestration are not yet wired.
- comet-ecc repo still has no remote, so code commit is local only.
