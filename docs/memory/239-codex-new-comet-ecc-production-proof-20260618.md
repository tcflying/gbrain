# 239-codex-new comet-ecc production proof gate

Recorded: 2026-06-18 17:39:55 China time

## Result

`G:\codex-project\comet-ecc` reached a verified strict/all/production audit pass for the current implementation.

Commits:

- `f1145c2 fix: verify real profile restoration by bytes`
- `921a57a feat: add production deploy proof gate`
- `5c24dcd fix: require platform-specific production proof`

## Implementation facts

- Added `production-deploy-proof`.
- `production-deploy-proof` requires `--apply-production`.
- It runs real-profile proof plus external-entry E2E and writes a proof artifact.
- It restores original profile files by default; `--keep-installed` is required to keep installed hooks.
- Real/production evidence is platform-specific for `codex`, `claude`, and `codebuddy`.
- A single Codex proof no longer satisfies all-platform production claims.

## Evidence

- Full production evidence: `G:\codex-project\comet-ecc-test-matrix\full-production-claim-evidence\latest-evidence.json`
- Full production audit: `G:\codex-project\comet-ecc-test-matrix\full-production-claim-audit\latest.json`

Audit result:

- `profile=strict`
- `platform=all`
- `claim_level=production`
- `claim_allowed=true`
- `passed=27`
- `failed=0`
- `git_clean=pass`

## Boundaries

- Real profile support is limited to `codex`, `claude`, and `codebuddy` until other platforms expose safe native user-profile schemas.
- `opencode`, `minimax-code`, `zcode`, `hermes`, and `workbuddy` are still bounded by project/profile E2E, sandbox external-entry proof, explicit home/schema gates, and doctor-only status where applicable.
