# Changes: FINCH task-081

Fix summary (from the fix record):

Full pass: grader note lets the judge accept a from-scratch layout and any formula structure that reproduces the source figures.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Task names exact cell coordinates for a workbook the agent has to build from scratch
  - Change: grader guidance task note: positions may differ from the reference (no seed workbook); the 'Other' header and the roll-ups down to Net Income are judged by meaning, not by cell address (I1, J-L, row 228).
- other finding, major, not in findings.json: 'Reinstate the missing formulas' does not say which formulas, and the GT's Consol logic and hardcodes can't be inferred from the source
  - Change: same task note: any formula structure reproducing the source figures is accepted, and the reference's hardcoded Consol cells may be values or formulas.
