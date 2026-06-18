# s69-mc-codex reference sample update

Recorded: 2026-06-19 China time
Owner/prefix: `s69-mc-codex-`

## User correction

The official content/output format reference is:

`C:\Users\datoo\Desktop\h红果与案例\《锦衣羽刃》一卡(1).docx`

Two additional works are good references only, for quality/craft/style rather
than official format:

1. `C:\Users\datoo\Desktop\h红果与案例\《机关术之八门之乱》正文(1).docx`
2. `C:\Users\datoo\Desktop\h红果与案例\《机关术之八门之乱》梗概和人物小传(1).docx`
3. `C:\Users\datoo\Desktop\h红果与案例\石慧彬-《鲜衣怒马醉华蓥》-3月30日-精修全本.docx`

## Local evidence

Project report:

`G:\codex-project\s69-mc-codex\docs\qa\reference-sample-review-20260619.md`

Project commit:

`53bf022b docs: record reference sample review`

## Reviewer calibration lesson

The current format gate/reviewer can run on these samples, but its hard-veto
results are not trustworthy as final sample-quality truth yet:

1. The existing format gate disagrees with the official Jinyi sample, so this is
   a validator calibration issue before it is a sample issue.
2. The existing drama splitter fails to recognize `第一集` style titles and can
   report 0 episodes.
3. The `multi_version` detector can hard-veto normal human script headings; it
   must be re-audited before using it against reference samples.

Operational rule: for future Jinyi/Yika or official-format work, treat
`《锦衣羽刃》一卡(1).docx` as source-of-truth format. Treat `机关术` and
`鲜衣怒马` as reference material, not as format replacements.
