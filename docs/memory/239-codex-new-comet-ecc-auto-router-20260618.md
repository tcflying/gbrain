# 239-codex-new comet-ecc auto router

Recorded: 2026-06-18 China time

Fact:

- comet-ecc now has one-command auto recognition and optional apply.
- Commit: `557f638 feat: add auto router command`

Command:

```text
python G:\codex-project\comet-ecc\comet_ecc.py auto --task "<task>" --project <repo> [--apply]
```

Behavior:

- Detect project language/framework markers.
- Classify task text.
- Select Comet-style phase.
- Select platform from explicit flag, `COMET_ECC_PLATFORM`, project marker, or Codex default.
- Plan by default; write only with `--apply`.

Evidence:

- `python -m py_compile G:\codex-project\comet-ecc\comet_ecc.py`
- `python -m pytest G:\codex-project\comet-ecc\tests\test_adapters.py` -> 4 passed
- `python G:\codex-project\comet-ecc\tests\e2e_matrix.py` -> passed

Boundary:

- One-command detect/install MVP is complete.
- Full Comet state-machine replacement is not complete.
