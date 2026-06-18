# s69-jc-codex writing references and corpus paths

Recorded: 2026-06-19 China time
Owner/prefix: `s69-jc-codex-`
Marker: `s69-jc-codex-writing-reference-stack-20260619`

User rule:
- For writing, format, review,素材, and writing-quality questions in this lane, first inspect the three user reference files, then SF/ANG references and the corpus/extraction paths below as needed.
- Record these facts in `G:\codex-project\s69-jc-codex\6.18.md`.

Primary writing reference files:
- `C:\Users\datoo\Desktop\h红果与案例\《锦衣羽刃》一卡(1).docx`
- `C:\Users\datoo\Desktop\xiezuo-172-skills\172skills-真复盘-怎么用提高写作.md`
- `C:\Users\datoo\Desktop\xiezuo-172-skills\novel.xlsx`

SF / StoryForge:
- GitHub: `https://github.com/91zgaoge/StoryForge`
- Claude clone: `G:\claude-project\storyforge-src`
- Codex ref: `G:\codex-project\_refs\StoryForge`
- Local verified origin: `https://github.com/91zgaoge/StoryForge.git`
- Local verified HEAD: `080bf4f`, `docs: 更新 CHANGELOG v0.8.1`
- User-provided characteristics: 23 stars, Tauri + Rust + React desktop, ISC in package.json but GitHub licenseInfo null, commercial subscription; use as mechanism reference, do not copy code without license review.

ANG / AI_NovelGenerator:
- GitHub: `https://github.com/YILING0013/AI_NovelGenerator`
- Claude clone: `G:\claude-project\ang-src`
- Codex ref: `G:\codex-project\_refs\AI_NovelGenerator`
- Local verified origin: `https://github.com/YILING0013/AI_NovelGenerator.git`
- Local verified HEAD: `170fde7`, `Merge pull request #228 from GuDong2003/docs/unify-readme-language-switcher`
- User-provided characteristics: 5168 stars, AGPL-3.0, Python CustomTkinter GUI + multi LLM adapter; read mechanisms only, AGPL code has commercial/copyleft risk.

Corpus and extraction sources:
- Raw book source root: `G:\小说\小说1`
- Copied premium corpus V2 / dynamics_library_v2: `G:\codex-project\octos-长篇小说\octos\data\optimizer\mmx\remote233_20260609_share_refresh\dynamics_library_v2`
- Copied batch root: `G:\codex-project\octos-长篇小说\octos\data\optimizer\mmx\remote233_20260609_share_refresh`
- Manifests:
  - `G:\codex-project\octos-长篇小说\octos\docs\qa\premium-corpus-v2-manifest.json`
  - `G:\codex-project\octos-长篇小说\octos\docs\qa\premium-corpus-v2-raw-manifest-20260609.json`
  - `G:\codex-project\octos-长篇小说\octos\docs\qa\premium-corpus-v2-quarantine-20260609.json`
- Main output root: `G:\codex-project\octos-长篇小说\octos\data\optimizer\mmx`
- Main structure library: `G:\codex-project\octos-长篇小说\octos\data\optimizer\mmx\dynamics_library_v2\m3_rich_extraction.live.jsonl`, verified non-empty rows `1551`
- Craft library: `G:\codex-project\octos-长篇小说\octos\data\optimizer\mmx\craft_library\m3_rich_extraction.live.jsonl`, verified non-empty rows `1555`
- Script blueprint library: `G:\codex-project\octos-长篇小说\octos\data\optimizer\mmx\script_blueprints\m3_rich_extraction.live.jsonl`, verified non-empty rows `1555`
- Done marker: `G:\codex-project\octos-长篇小说\octos\data\optimizer\mmx\dynamics_library_v2\m3_rich_extraction.live.done`, verified non-empty rows `1555`
- Autoscheduler route manifest: `G:\codex-project\octos-长篇小说\octos\docs\qa\source-route-manifest-autoscheduler-latest.json`
- Local3090 teacher baseline extraction is separate and must not be mixed with the above: `G:\codex-project\octos-长篇小说\octos\data\optimizer\mmx\local3090_m3_teacher_baseline\...`

Operational impact:
- Prefer historical/reference lookup before new writing fixes.
- V2 feature/craft/script data is resource material, not current-book writer source truth.
- Keep Local3090 teacher baseline separate from V2/main extraction outputs.
