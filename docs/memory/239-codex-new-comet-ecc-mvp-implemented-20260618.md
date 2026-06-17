# 239-codex-new comet-ecc MVP implemented and Codex-tested

Recorded: 2026-06-18 China time
Owner/prefix: `239-codex-new-`
Marker: `239-codex-new-comet-ecc-mvp-implemented-20260618`

## Implementation

Created `G:\codex-project\comet-ecc` as an independent comet-ecc MVP.

Local git state:

- Branch: `239-codex-new`
- Commit: `0ccf48b feat: add comet ecc codex hook mvp`
- Remote: none configured, so no push was possible.

Files:

- `G:\codex-project\comet-ecc\comet_ecc.py`
- `G:\codex-project\comet-ecc\README.md`
- `G:\codex-project\comet-ecc\docs\codex-e2e-20260618.md`
- Updated design report: `G:\codex-project\comet-ecc-hooks-design-20260618.md`

## Implemented commands

- `doctor`: checks Comet/ECC source paths, report file, platform runtime hints, adapter plans.
- `catalog`: reads ECC commands/agents/skills/rules/hooks catalog.
- `select`: detects repo language/framework markers and suggests ECC packs.
- `install-hooks`: writes Codex `.codex/hooks.json`; other platforms dry-run only.
- `uninstall-hooks`: removes Codex comet-ecc managed hook.
- `status`: checks Codex hook installation.
- `run-hook`: Codex PreToolUse safe guard runner.

## Adapter state

- Codex: write-supported native command hooks with `commandWindows`.
- Claude Code: experimental plan only.
- OpenCode: dry-run native plugin plan.
- MiniMax Code: modeled as `opencode-backed-desktop`; doctor/dry-run only until writable config path is confirmed.
- ZCode: skills/commands dry-run only; native hook schema pending.
- CodeBuddy Code CLI: experimental plan only.
- WorkBuddy Desktop: doctor only; schema pending.

## Codex E2E evidence

Test repo:

- `G:\codex-project\comet-ecc-test-codex`

Hook file written:

- `G:\codex-project\comet-ecc-test-codex\.codex\hooks.json`

Evidence file:

- `G:\codex-project\comet-ecc\docs\codex-e2e-20260618.md`

Passed checks:

1. `python -m py_compile G:\codex-project\comet-ecc\comet_ecc.py`
2. `doctor/catalog/select`
3. Codex install dry-run
4. Codex actual install
5. `status` returned `comet_ecc_installed=true`
6. Hook runner allowed `python --version`
7. Hook runner denied PowerShell `$_`
8. Hook runner denied `git reset --hard`
9. All adapter dry-runs returned rc=0.

## Current boundary

Only Codex writes are enabled. Other platforms must remain dry-run/doctor until platform-specific E2E proves safe config paths and hook behavior.
