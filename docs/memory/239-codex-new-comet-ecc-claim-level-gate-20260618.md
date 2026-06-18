# 239-codex-new-comet-ecc-claim-level-gate-20260618

Recorded: 2026-06-18 16:55:37 中国时间
Owner/prefix: `239-codex-new-`

## Durable fact

comet-ecc now has a claim-level overclaim gate.

Implemented commit:

- `935a6ef feat: gate audit claims by level`

Claim levels:

- `local`: local strict evidence only.
- `real`: requires `real_profile_e2e` and `external_execution_e2e`.
- `production`: requires `real_profile_e2e`, `external_execution_e2e`, and `production_deploy_proof`.

Final evidence:

- Local strict/all audit: `claim_allowed=true`, `passed=20`, `failed=0`, `command_count=13`.
- Production claim audit: `claim_allowed=false`, `passed=20`, `failed=3`.
- Production blocked codes: `evidence_real_profile_e2e`, `evidence_external_execution_e2e`, `evidence_production_deploy_proof`.

Evidence paths:

- `G:\codex-project\comet-ecc-test-matrix\final-claim-local-evidence\latest-evidence.json`
- `G:\codex-project\comet-ecc-test-matrix\final-claim-local-audit\latest.json`
- `G:\codex-project\comet-ecc-test-matrix\final-claim-production-evidence\latest-evidence.json`
- `G:\codex-project\comet-ecc-test-matrix\final-claim-production-audit\latest.json`
- `G:\codex-project\comet-ecc-hooks-design-20260618.md`

Boundary:

- Current comet-ecc proof is strong local strict/all proof.
- It is not real external IDE execution proof.
- It is not production deployment proof.
- Future production-ready claims must include explicit successful production evidence entries.
