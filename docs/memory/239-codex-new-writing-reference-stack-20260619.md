# 239-codex-new writing reference stack

Recorded: 2026-06-19 China time
Owner/prefix: `239-codex-new-`

## Rule

For writing-related problems, especially 一卡, Hongguo short drama, review, format validation, writing skills, and corpus/resource injection, first consult:

1. `C:\Users\datoo\Desktop\h红果与案例\《锦衣羽刃》一卡(1).docx`
2. `C:\Users\datoo\Desktop\xiezuo-172-skills\172skills-真复盘-怎么用提高写作.md`
3. `C:\Users\datoo\Desktop\xiezuo-172-skills\novel.xlsx`

Also use `G:\claude-project\octos-GA\docs\6.18.md` and its linked Claude sessions as the prior-answer source.

## Reference repos

- SF / StoryForge: `https://github.com/91zgaoge/StoryForge`; local `G:\claude-project\storyforge-src`; Codex ref `G:\codex-project\_refs\StoryForge`; HEAD `080bf4f`; Tauri + Rust + React desktop; ISC package but GitHub licenseInfo null and subscription-commercial signals.
- ang / AI_NovelGenerator: `https://github.com/YILING0013/AI_NovelGenerator`; local `G:\claude-project\ang-src`; Codex ref `G:\codex-project\_refs\AI_NovelGenerator`; HEAD `170fde7`; AGPL-3.0 Python + CustomTkinter + multi-LLM adapter, strong commercial/copyleft risk.

## Corpus paths

- Source root: `G:\小说\小说1`
- Premium V2 copied root: `G:\codex-project\octos-长篇小说\octos\data\optimizer\mmx\remote233_20260609_share_refresh`
- Premium V2 dynamics: `G:\codex-project\octos-长篇小说\octos\data\optimizer\mmx\remote233_20260609_share_refresh\dynamics_library_v2`
- Manifests: `premium-corpus-v2-manifest.json`, `premium-corpus-v2-raw-manifest-20260609.json`, `premium-corpus-v2-quarantine-20260609.json` under `G:\codex-project\octos-长篇小说\octos\docs\qa`
- Extracted root: `G:\codex-project\octos-长篇小说\octos\data\optimizer\mmx`
- Dynamics live: `dynamics_library_v2\m3_rich_extraction.live.jsonl` = 1551 records
- Craft live: `craft_library\m3_rich_extraction.live.jsonl` = 1555 records
- Script blueprints live: `script_blueprints\m3_rich_extraction.live.jsonl` = 1555 records
- Done marker: `dynamics_library_v2\m3_rich_extraction.live.done` = 1555 records
- Autoscheduler route manifest: `G:\codex-project\octos-长篇小说\octos\docs\qa\source-route-manifest-autoscheduler-latest.json`
- Local3090 teacher baseline is separate: `G:\codex-project\octos-长篇小说\octos\data\optimizer\mmx\local3090_m3_teacher_baseline\...`
