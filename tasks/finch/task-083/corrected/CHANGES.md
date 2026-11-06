# Changes: FINCH task-083

Fix summary (from the fix record):

Guidance note accepts either lag/lead direction and 6 or 7 lead rows.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Lag/lead direction is never defined, and only the answer key's convention can pass
  - Change: graderGuidance: task note after the opening paragraph states the reference's lag/lead direction and accepts the opposite convention applied consistently.
- other finding, major, not in findings.json: AI grader (production): rejects a valid answer on "overall grade"
  - Change: graderGuidance: task note after the opening paragraph states the reference's lag/lead direction and accepts the opposite convention applied consistently.
- other finding, major, not in findings.json: Problem statement gives two different lead horizons: 1–6 months, then 1–7 months
  - Change: graderGuidance: the same task note accepts 6 or 7 lead rows.
