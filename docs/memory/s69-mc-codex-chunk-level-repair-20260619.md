# s69-mc-codex chunk-level repair hardening - 2026-06-19

- Owner/prefix: `s69-mc-codex-`
- Repo/worktree: `G:\codex-project\s69-mc-codex`
- Branch/remote: `s69-mc-codex` -> `octosgh/s69-mc-codex`
- Commit: `60aebef5 fix(writer): implement chunk-level repair`
- QA record: `G:\codex-project\s69-mc-codex\docs\qa\chunk-level-repair-20260619.md`

## Durable lesson

Missing-episode and multi-version duplicate-output defects are chunk-scope failures. They must be repaired against the contiguous multi-episode chunk and then fully re-split/re-verified. Single-episode repair prompts must refuse these defects because they lack enough context to safely reconstruct or merge the sequence.

## Implementation evidence

- `services/writer/octos_writer/repair.py` keeps `missing_episode` and `multi_version` as `scope=chunk`, adds `repair_chunk(...)`, and fail-closes single-episode `repair(...)` for chunk breaks.
- `services/writer/octos_writer/chunk.py` attempts at most one chunk-level repair in production `require_ready=True` flow, then re-verifies each episode. Probe mode preserves full failed-batch evidence without repair.
- `619.md`, `619todo.md`, and `docs/qa/chunk-level-repair-20260619.md` record the batch.

## Verification

- Sartre subagent final review: 0 issues / LGTM.
- `python -m pytest services\writer\tests\test_repair.py services\writer\tests\test_chunk_safety.py services\writer\tests\test_finalize.py -q` -> 10 passed.
- `python -m pytest services\writer\tests -q -k "not live"` -> 69 passed, 2 deselected.
- `python -m pytest services\determ\tests\test_verify_facade.py services\determ\tests\test_drama_rating.py -q` -> 12 passed.
- `python -m pytest services\review\tests -q` -> 9 passed.
- `python -m py_compile services\writer\octos_writer\repair.py services\writer\octos_writer\chunk.py services\writer\tests\test_repair.py services\writer\tests\test_chunk_safety.py` -> passed.
- `codegraph sync` -> already up to date.

## Follow-up

Continue with provider/runtime hardening: Codex JSON event parsing, proxy policy, timeout/error classification, then live writing tests only after hardening gates are closed.
