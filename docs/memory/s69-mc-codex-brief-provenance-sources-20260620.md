# s69-mc-codex brief provenance source hardening

Recorded: 2026-06-20 01:24 China time
Owner/prefix: `s69-mc-codex-`

Project/worktree: `G:\codex-project\s69-mc-codex`
Branch: `s69-mc-codex`
Commit: `28c0ea5e fix(writer): harden brief provenance sources`

## Lesson

Production brief provenance must fail closed with structured evidence when the sidecar manifest points to an invalid source file. A source path that exists but is a directory or non-regular file is not allowed to reach `sha256_file()` and throw an uncaught exception.

## Current behavior

- Non-file source path: `source_file_not_file`
- Hash read `OSError`: `source_sha256_unreadable`
- Overall result: `brief_provenance_invalid`

## Evidence

- Code: `services/writer/octos_writer/brief_provenance.py`
- Regression: `services/writer/tests/test_candidate_brief.py::test_brief_provenance_rejects_source_directory_without_crashing`
- RED proof: old code raised `PermissionError` on a directory source path.
- Verification: writer full `260 passed, 2 skipped`; determ `56 passed`; review `9 passed`.
- Subagent: `Kierkegaard` APPROVE, 0 findings.

No live provider was started and no 40/80-episode production claim was made.
