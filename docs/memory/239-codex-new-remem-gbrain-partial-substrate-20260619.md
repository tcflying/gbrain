# 239-codex-new remem standalone project and gbrain boundary

Recorded: 2026-06-19 China time
Owner/prefix: `239-codex-new-`
Marker: `239-codex-new-remem-gbrain-partial-substrate-20260619`

## Summary

The WeChat reflection-memory project is being implemented as standalone
`G:\codex-project\remem`, independent from comet-ecc.

## remem evidence

- Path: `G:\codex-project\remem`
- Branch: `239-codex-new`
- Commit: `d1d7a7407c5c2ededd1e5d3a64cc541fac242782`
- Tests: `python -m compileall remem tests`; `python -m unittest discover -s tests`; CLI smoke with `--threshold 1`.

## gbrain boundary

Answer class: `partial_fix`.

gbrain already provides durable memory/capture/search/recall/conversation
extraction and cycle substrate. It does not yet prove the exact agent-side
reflection loop from the article: real session event intake, completed-round
counter, every-N-round trigger, per-session `last_reflected_round`, and
correction/rule promotion gate.

Decision: keep `remem` as a thin event/reflection layer and use gbrain as an
optional durable sink. Upstream only after the hook loop is proven.
