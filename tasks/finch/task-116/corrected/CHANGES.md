# Changes: FINCH task-116

Fix summary (from the fix record):

Guidance now accepts the N. TEXAS ERCOT peak column (7 same / 3 opposite / 2 neither) as well as the reference's HL&P column.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Unclear which column is 'ERCOT peak', and the two columns give different graded answers
  - Change: graderGuidance: appended to the opening paragraph a sentence accepting N. TEXAS as the ERCOT peak column with Same 7 / Opposite 3 / 2 neither (recomputed from the source: HL&P gives 8/2/2, N. TEXAS 7/3/2).
