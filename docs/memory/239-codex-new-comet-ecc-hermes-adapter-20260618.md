# 239-codex-new comet-ecc Hermes adapter

Recorded: 2026-06-18 China time

Fact:

- User added Hermes Agent to comet-ecc platform scope.
- Hermes is a first-class agent/orchestrator adapter for comet-ecc.
- It should not be treated as only another IDE.

Local Hermes evidence:

- Home: `C:\Users\datoo\AppData\Local\hermes`
- Profiles: `C:\Users\datoo\AppData\Local\hermes\profiles`
- Skills: `C:\Users\datoo\AppData\Local\hermes\skills`
- Hooks: `C:\Users\datoo\AppData\Local\hermes\hooks`
- Config: `C:\Users\datoo\AppData\Local\hermes\config.yaml`
- Kanban DB: `C:\Users\datoo\AppData\Local\hermes\kanban.db`

comet-ecc implementation:

- Repo: `G:\codex-project\comet-ecc`
- Commit: `306c805 feat: add hermes adapter plan`
- Adapter id: `hermes`
- Capabilities: `skills`, `profiles`, `plugin-hooks`, `shell-hooks`, `kanban`, `mcp`, `acp`
- Install status: `dry-run-plan`

Safety boundary:

- Do not directly mutate Hermes `kanban.db` or `state.db`.
- Shell hooks require explicit allowlist / acceptance.
- Hermes write support must wait for Hermes-specific E2E.

Evidence files:

- `G:\codex-project\comet-ecc\docs\codex-e2e-20260618.md`
- `G:\codex-project\comet-ecc-hooks-design-20260618.md`
