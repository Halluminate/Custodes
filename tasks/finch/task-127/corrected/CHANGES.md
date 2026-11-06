# Changes: FINCH task-127

Fix summary (from the fix record):

The reference averaged the Glenrock payables over Jan-Jun 2002 but the two Ignacio deals with the same term over Jan-May only, and the Summary footnote described a different, price-based method. The Ignacio averages now include the June row, one prompt sentence points to the Exposure sheet, and the guidance states the window and allows either sign.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- reference/gt_127_ref_0.xlsx

## Fixed

- [F2](../findings.json) (Task Spec): Contradictory and ambiguous definition of '55 days payables' between prompt, workbook footnote, and ground truth
  - Change: gt_127_ref_0.xlsx: Summary!F15 =-AVERAGE(Exposure!H7:H12), F16 =-AVERAGE(Exposure!I7:I12) (were rows 7-11), the same window as F13. F17 and F20 recalculated (-8,079,628.19 and -8,928,672.26). Prompt: one sentence added saying to take payables from the Exposure sheet, not the footnote formula. Guidance: task note on the averaging window.
- [F3](../findings.json) (Verification): Ground truth averages the payables of contracts with the same term over different windows (Glenrock uses 6 months, the two Ignacio deals use 5)
  - Change: Same GT edit: all three 31-May-2002 contracts now average Exposure rows 7-12.
- [F1](../findings.json) (Verification): Reference payables calculations contradict the workbook’s stated calculation rule
  - Change: Prompt sentence: 'Take the payables from the Exposure sheet rather than from the price formula described in the Summary footnote.' Guidance note allows either sign for the payables.
