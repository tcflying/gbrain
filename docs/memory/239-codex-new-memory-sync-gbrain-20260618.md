# 239-codex-new memory sync must include gbrain

Recorded: 2026-06-18 China time
Owner/prefix: `239-codex-new-`
Marker: `239-codex-new-memory-sync-include-gbrain-20260618`

## User rule

Future durable memory writes must include gbrain in addition to the existing memory targets.

## Required memory targets after this rule

When Codex learns a durable fact, correction, workflow rule, model/provider decision, implementation result, bug lesson, E2E conclusion, or phase decision, write it to:

1. Codex memory note under `C:\Users\datoo\.codex\memories\extensions\ad_hoc\notes\`.
2. MemSearch markdown under `C:\Users\datoo\.memsearch\memory\`, then refresh the whole memory directory with `memsearch index C:\Users\datoo\.memsearch\memory`.
3. Paperclip markdown memory `G:\codex-project\paperclip\claudemem.md`, with scoped commit and push.
4. Codex global standing rules `C:\Users\datoo\.codex\AGENTS.md` when the fact changes future Codex behavior.
5. gbrain memory/truth source under `G:\claude-project\gbrain`, using Codex-owned prefixed files such as `docs\memory\239-codex-new-*.md`.

## gbrain write boundary

- Do not rewrite existing Claude-owned or dirty gbrain files.
- Prefer creating or appending a Codex-owned file with prefix `239-codex-new-`.
- If gbrain has unrelated dirty files, stage only the new/changed Codex-owned memory file.
- Commit/push gbrain memory only when it is safe and scoped; otherwise report the exact dirty/blocking status.
