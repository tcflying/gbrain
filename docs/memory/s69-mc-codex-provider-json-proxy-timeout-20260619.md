# s69-mc-codex provider JSON/proxy/timeout hardening - 2026-06-19

- Owner/prefix: `s69-mc-codex-`
- Repo/worktree: `G:\codex-project\s69-mc-codex`
- Branch/remote: `s69-mc-codex` -> `octosgh/s69-mc-codex`
- Commit: `69f84664 fix(writer): harden provider JSON and timeout handling`
- QA record: `G:\codex-project\s69-mc-codex\docs\qa\provider-json-proxy-timeout-20260619.md`

## Durable lesson

Provider wrapper failures must remain provider route/proof evidence, not story content evidence. Clean writer wrappers must preserve Codex JSON final agent-message output, direct/no-proxy policy, and timeout classification before live writing tests.

## Implementation evidence

- `services/writer/octos_writer/providers.py` now calls `codex exec --json`, parses final `item.completed.item.type=agent_message`, supports delta-only and assistant JSON events, and filters thinking/tool content.
- `providers._direct_env(...)` strips proxy variables from Codex writer subprocesses and sets `NO_PROXY=*` / `no_proxy=*`.
- `providers._env_int(...)` safely parses `OCTOS_CODEX_TIMEOUT_S`.
- `provider_errors.py`, `mmx_client.py`, and `providers.py` classify timeout transport failures separately from generic network failures; Codex timeout keeps stdout/stderr tails.
- `619.md`, `619todo.md`, and `docs/qa/provider-json-proxy-timeout-20260619.md` record the batch.

## Verification

- Pascal subagent final review: CRITICAL 0, HIGH 0, MEDIUM 0, LOW 0.
- `python -m pytest services\writer\tests\test_mmx_client.py services\writer\tests\test_providers.py -q` -> 18 passed.
- `python -m pytest services\writer\tests -q -k "not live"` -> 78 passed, 2 deselected.
- `python -m pytest services\determ\tests\test_verify_facade.py services\determ\tests\test_drama_rating.py -q` -> 12 passed.
- `python -m pytest services\review\tests -q` -> 9 passed.
- `python -m py_compile services\writer\octos_writer\provider_errors.py services\writer\octos_writer\mmx_client.py services\writer\octos_writer\providers.py services\writer\tests\test_mmx_client.py services\writer\tests\test_providers.py` -> passed.
- `codegraph sync` -> already up to date.

## Follow-up

Official staged spine / character bible generation and final DOCX packaging remain blockers before live 40-episode writing tests.
