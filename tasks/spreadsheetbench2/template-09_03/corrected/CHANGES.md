# Changes: SpreadsheetBench 2 template-09_03

Fix summary (from the fix record):

The cell check failed a model that shows the debt-schedule Interest Expense rows (D24:H24, D32:H32) as positive amounts and negates them in the cash-flow table; nothing in the sheet fixes that sign. Those 10 cells are now left out of answer_position (rows 10 and 11 still check the interest). The key's junior-debt repayment formula (D28:H28) had a sign error that made repayment impossible; it is corrected, and its values stay 0 in this dataset.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_09_03_golden.xlsx

## Fixed

- other finding, major, not in findings.json: Undisclosed sign convention for Interest Expense rows in Senior and Junior Debt Schedules (D24:H24 and D32:H32)
  - Change: answer_position 'Sheet'!B2:H36 -> "'Sheet'!B2:H23,'Sheet'!B24:C24,'Sheet'!B25:H31,'Sheet'!B32:C32,'Sheet'!B33:H36" (drops D24:H24 and D32:H32). Real scorer with the patched golden: golden 1.0; input + key formulas 1.0; input + key with positive schedule interest and rows 10/11 negated 1.0 (was 0.0, modification 0.8507); untouched input 0.0 (57 errors).
- other finding, minor, not in findings.json: The ground-truth junior debt repayment formula has a sign error, so junior debt can never be repaid
  - Change: gt_09_03_golden.xlsx Sheet!D28:H28: MIN(0,D15-D19-D20) -> MIN(0,-(D15+D19+D20)) (same for E..H), so junior debt is repaid from cash left after senior payments once senior is retired. XML-level edit, nothing else changed; LibreOffice recalc keeps D28:H28 = 0 (senior H21 = 7.87 is never retired), so every graded value is unchanged.
