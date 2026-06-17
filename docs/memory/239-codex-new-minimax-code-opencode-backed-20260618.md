# 239-codex-new MiniMax Code is OpenCode-backed on this machine

Recorded: 2026-06-18 China time
Owner/prefix: `239-codex-new-`
Marker: `239-codex-new-minimax-code-opencode-backed-20260618`

## Correction

MiniMax Code desktop should not be modeled as only `skills auto-discovery` or `schema_pending`.
On this machine it is OpenCode-backed: MiniMax Code starts an embedded OpenCode runtime.

## Evidence

1. Public source:
   - MiniMax Agent changelog mentions `Fixed OpenCode session state lost after restart (session not found)`, proving OpenCode session/runtime compatibility is part of MiniMax Code behavior.
   - MiniMax skills repository includes `.opencode` layout in addition to `.codex`, `.claude-plugin`, and `.cursor-plugin`.

2. Local process evidence on 2026-06-18:
   - MiniMax app: `G:\MiniMax\MiniMax Code\MiniMax Code.exe`
   - Electron user data: `C:\Users\datoo\AppData\Roaming\MiniMax`
   - MiniMax daemon: `G:\MiniMax\MiniMax Code\resources\resources\daemon\daemon.js --port 15321`
   - Embedded OpenCode runtime: `G:\MiniMax\MiniMax Code\resources\resources\opencode\opencode.exe serve --port 18924`

## Implementation impact for comet-ecc

1. `minimax-code` adapter must be classified as `opencode-backed-desktop`.
2. First strategy: reuse OpenCode plugin/skills adapter ideas.
3. Doctor must detect MiniMax Code process, embedded `opencode.exe`, port, and writable config/plugin/skills locations.
4. Do not write directly into `C:\Users\datoo\AppData\Roaming\MiniMax` internal app data or databases.
5. If MiniMax Code does not read standard `.opencode/plugins`, fall back to MiniMax skill auto-discovery.
6. Do not assume port `18924` is permanent; treat it as observed current runtime evidence.

## Updated report

`G:\codex-project\comet-ecc-hooks-design-20260618.md` now includes this correction.
