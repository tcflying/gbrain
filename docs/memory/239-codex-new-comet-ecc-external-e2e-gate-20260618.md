# 239-codex-new-comet-ecc-external-e2e-gate-20260618

Recorded: 2026-06-18 17:10:02 中国时间
Owner/prefix: `239-codex-new-`

## Durable fact

comet-ecc now has a sandbox external execution E2E gate.

Implemented commit:

- `d5dd69d feat: add sandbox external e2e evidence`

What changed:

- Added CLI command `external-e2e`.
- `external-e2e --platform all` installs sandbox adapter surfaces and verifies each platform without mutating real user profiles.
- Hook-capable platforms execute the safe hook runner fixture and verify both allow and deny decisions.
- Skill-only platforms verify generated skill entry surfaces.
- WorkBuddy remains doctor-only until native schema proof exists.
- `audit --run-evidence --claim-level real` now auto-generates `external_execution_e2e`.
- It intentionally does not auto-generate `real_profile_e2e` or `production_deploy_proof`.

Final evidence:

- Unit tests: `29 passed`.
- Full E2E matrix: `python tests\e2e_matrix.py` passed.
- External all-platform E2E: `external-e2e --platform all` passed.
- Security scan: `0 findings`.
- Strict local clean audit: `claim_allowed=true`, `passed=20`, `failed=0`, `git_clean=pass`.
- Real claim clean audit: `claim_allowed=false`, only failed code `evidence_real_profile_e2e`; `evidence_external_execution_e2e` passed.

Evidence paths:

- `G:\codex-project\comet-ecc-test-matrix\final-external-local-evidence-serial\latest-evidence.json`
- `G:\codex-project\comet-ecc-test-matrix\final-external-local-audit-serial\latest.json`
- `G:\codex-project\comet-ecc-test-matrix\final-external-real-evidence\latest-evidence.json`
- `G:\codex-project\comet-ecc-test-matrix\final-external-real-audit\latest.json`
- `G:\codex-project\comet-ecc-hooks-design-20260618.md`

Boundary:

- This is sandbox external-entry proof, not real user profile mutation proof.
- This is not production deployment proof.
- Do not mark the overall comet-ecc perfect goal complete until real-profile and production proof gates are satisfied or deliberately scoped out by the user.
