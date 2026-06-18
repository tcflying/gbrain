# s69-mc-codex official yika package and DOCX delivery - 2026-06-19

- Owner/prefix: `s69-mc-codex-`
- Repo/worktree: `G:\codex-project\s69-mc-codex`
- Branch/remote: `s69-mc-codex` -> `octosgh/s69-mc-codex`
- Commit: `94f1851e feat(writer): package official yika deliverables`
- QA record: `G:\codex-project\s69-mc-codex\docs\qa\official-yika-package-docx-20260619.md`

## Durable lesson

Official 一卡 delivery is not complete with only renderer auto-fill or Markdown. It needs explicit staged project metadata and a bundle containing Markdown, DOCX, and package manifest. For the current complete-delivery target, missing DOCX export is a hard delivery failure.

## Implementation evidence

- `services/writer/octos_writer/project_package.py` builds explicit `spine`, `character_bible`, and normalized `synopsis_episodes`.
- `finalize.gate_run(...)` stores `out["project_package"]` and renders official yika from that package.
- `yika_format.render_from_run(...)` prefers explicit package fields and falls back to old auto-fill only when package data is absent.
- `services/writer/octos_writer/delivery.py` exports `.md`, `.docx`, and `.package.json` with sha256, format report, project package, and export status.
- `run_matrix.py`, `run_drive.py`, and `run_chunk.py` export before writing run JSON so `official_yika_exports` is persisted; official yika text with export failure makes the runner fail.
- `619.md`, `619todo.md`, and `docs/qa/official-yika-package-docx-20260619.md` record the batch.

## Verification

- Mill subagent final review: CRITICAL 0, HIGH 0, MEDIUM 0, LOW 0.
- `python -m pytest services\writer\tests\test_yika_format.py services\writer\tests\test_delivery.py services\writer\tests\test_runner_format_profile.py -q` -> 39 passed.
- `python -m pytest services\writer\tests -q -k "not live"` -> 80 passed, 5 deselected.
- `python -m pytest services\determ\tests\test_verify_facade.py services\determ\tests\test_drama_rating.py -q` -> 12 passed.
- `python -m pytest services\review\tests -q` -> 9 passed.
- Py compile passed.
- CodeGraph synced.

## Follow-up

Run a hardening readiness audit over remaining todo items and choose the first low-risk writing test route before live 40-episode writing.
