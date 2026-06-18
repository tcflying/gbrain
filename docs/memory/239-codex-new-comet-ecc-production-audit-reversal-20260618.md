# 239-codex-new comet-ecc production audit reversal

Recorded: 2026-06-18 22:45 China time
Owner/prefix: `239-codex-new-`

## Summary

The earlier `comet-ecc` "perfect" claim was superseded. A reverse audit found that production evidence needed stronger semantic validation and safer generation controls.

## Findings

1. Command-name plus return-code evidence was insufficient for real/production proof.
2. Production proof output needed redaction/summarization to avoid leaking existing profile config into evidence.
3. `audit --run-evidence --claim-level production` needed an explicit real-profile evidence switch.

## Fix

Repo: `G:\codex-project\comet-ecc`
Branch: `239-codex-new`
Commits:

1. `a79f67f fix: redact production proof output`
2. `490875e fix: gate production evidence generation`

Current rule:

1. Real/production audit proof requires parseable stdout JSON.
2. `profile_home_override=true` cannot satisfy real/production claim evidence.
3. `--run-evidence` does not mutate real profiles by default.
4. `--apply-real-profile-evidence` is required for generated real-profile and production proof commands.

Final proof:

1. `G:\codex-project\comet-ecc-test-matrix\full-production-semantic-evidence\latest-evidence.json`
2. `G:\codex-project\comet-ecc-test-matrix\full-production-semantic-audit\latest.json`
3. Result: `strict/all/production`, `claim_allowed=true`, `passed=27`, `failed=0`, generated command count `20`.
