# 239-codex-new comet-ecc OpenSpec refresh to 11 Codex skills

Recorded: 2026-06-19 China time
Owner/prefix: `239-codex-new-`

## Fact

Rerunning OpenSpec init in `G:\codex-project\comet-ecc` refreshed Codex support from 5 skills to 11 skills.

Command:

`openspec init --tools codex`

Commit:

`7a5889b chore: refresh openspec codex skills`

## New skills

1. `openspec-bulk-archive-change`
2. `openspec-continue-change`
3. `openspec-ff-change`
4. `openspec-new-change`
5. `openspec-onboard`
6. `openspec-verify-change`

## Verification

`openspec list --json` returned `{"changes":[]}` and `G:\codex-project\comet-ecc` was clean after commit.

No remote is configured for `G:\codex-project\comet-ecc`.
