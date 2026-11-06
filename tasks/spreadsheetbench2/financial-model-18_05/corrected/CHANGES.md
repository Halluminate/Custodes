# Changes: SpreadsheetBench 2 financial-model-18_05

Fix summary (from the fix record):

The golden workbook added an unrequested 'Esc. %' label at P&L!A13 inside the graded range, so every run that followed the instructions failed the all-or-nothing modification check. The label is removed from the GT, so A13 matches the blank input.

Changed files (in this folder):

- reference/gt_18_RoadAssets_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check returns false negative (score 0.0) on correct solutions in units 1 and 3 due to P&L!A13 discrepancy
  - Change: gt_18_RoadAssets_golden.xlsx P&L!A13: removed the unrequested label 'Esc. %' (cell now empty, style kept; it is blank in the input), no other cell changed. A13 is now a regression cell, so runs that leave it blank pass. Local verifier grade: new GT 1.0/1.0, and the old GT (with the label) still passes as an output under the 99.8% regression allowance.
- [F1](../findings.json) (Task Spec): Verifier enforces unstated edit at P&L!A13 ('Esc. %') that is absent from input and task instructions
  - Change: Same GT edit (P&L!A13 'Esc. %' removed).
- [F2](../findings.json) (Verification): Ground truth adds a label nobody asked for (P&L!A13 'Esc. %'), so the all-or-nothing check fails correct solutions
  - Change: Same GT edit (P&L!A13 'Esc. %' removed).
- [F3](../findings.json) (Task Spec): Verifier requires an unrequested P&L header change
  - Change: Same GT edit (P&L!A13 'Esc. %' removed).
