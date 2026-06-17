# 239-codex-new comet-ecc adapter E2E matrix

Recorded: 2026-06-18 China time

Fact:

- comet-ecc now has automated adapter install tests and matrix E2E.
- Commit: `8791aa4 feat: test adapter installs across platforms`

Adapter matrix:

- Codex: `.codex/hooks.json`
- Claude Code: `.claude/settings.local.json`
- OpenCode: `.opencode/plugins/comet-ecc.ts`
- MiniMax Code: `.minimax-code/skills/comet-ecc/SKILL.md` fallback only
- ZCode: `.zcode/skills/comet-ecc/SKILL.md` fallback only
- CodeBuddy: `.codebuddy/settings.local.json`
- WorkBuddy: doctor only
- Hermes: explicit `COMET_ECC_HERMES_HOME`, no `kanban.db` / `state.db` mutation

Evidence:

- `python -m py_compile G:\codex-project\comet-ecc\comet_ecc.py`
- `python -m pytest G:\codex-project\comet-ecc\tests\test_adapters.py` -> 2 passed
- `python G:\codex-project\comet-ecc\tests\e2e_matrix.py` -> all platform commands returned 0

Boundary:

- Native user-profile writes remain gated until real-profile E2E.
- comet-ecc repo has no remote; commit is local only.
