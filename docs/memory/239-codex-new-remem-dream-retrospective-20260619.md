# 239-codex-new remem dream retrospective requirement

Recorded: 2026-06-19 06:05 China time

User added a durable remem requirement: the project-local memory system should
also support automatic retrospective / dream consolidation.

Project update:

1. `G:\codex-project\remem\ROADMAP.md` now includes
   `V4.5: Dream Retrospective Loop`.
2. `G:\codex-project\remem\docs\dream-retrospective-design.md` records the
   comparison and design boundary.
3. remem commit: `9a68e57 docs: add dream retrospective loop`.
4. Verification: `python -m unittest discover -s tests` passed, 16 tests.

Design boundary:

1. `remem dream` should run offline or by manual command, not block active
   sessions.
2. It should stay project-local by default and write reviewable candidates
   before promotion.
3. It should consolidate repeated lessons, detect contradictions, mark stale or
   superseded memories, and propose checklist/test/validator/skill/hook-policy
   candidates.
4. Global export and active policy rollout remain gated by V2/V3/V5.

External comparison:

1. Claude Code provides official auto memory and hooks, but no verified
   official first-party `dream` command was found.
2. GBrain has a real `gbrain dream` command and local scheduled wiring on this
   machine.
3. Hermes Agent has memory, session search, cron, curator, and memory
   providers; Auto Dream / Dreaming is public issue/proposal evidence unless
   verified in the installed runtime.
