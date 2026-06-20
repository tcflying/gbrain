# s69-mc-codex candidate brief approval blocker

Recorded: 2026-06-20 China time
Owner/prefix: s69-mc-codex-

## Fact

The current candidate story brief is not approved for production.

- Candidate brief: `G:\codex-project\s69-mc-codex\docs\qa\candidate-brief-jiguanshu-20260619.md`
- Manifest: `G:\codex-project\s69-mc-codex\docs\qa\candidate-brief-jiguanshu-20260619.manifest.json`
- Manifest status: `candidate_status=candidate_only`, `approved_for_production=false`, `approval.reason=brief_candidate_not_approved`.
- Codex must not promote or use this candidate as `OCTOS_BRIEF_FILE` unless the user explicitly approves this exact brief/topic.

## If user approves

Only after explicit user approval, use:

`python services\writer\promote_candidate_brief.py --candidate docs\qa\candidate-brief-jiguanshu-20260619.md --out <approved-brief.md> --approved-by <user> --approval-note <note>`

Then refresh MiniMax/M3 quota proof and rerun `preflight_40.py` before any live provider writing.

## Evidence

- Project log commit: `bcfd065d3 docs: record candidate brief approval blocker`
- CodeGraph sync completed after the log update.
