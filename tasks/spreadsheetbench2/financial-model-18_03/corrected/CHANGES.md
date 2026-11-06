# Changes: SpreadsheetBench 2 financial-model-18_03

Fix summary (from the fix record):

The golden workbook added an unrequested 'Esc. %' label at P&L!A13 inside the graded range, so every run that followed the instructions failed the all-or-nothing modification check. The label is removed from the GT, so A13 matches the blank input.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_18_RoadAssets_golden.xlsx

## Fixed

- [F2](../findings.json) (Task Spec): Ground truth adds an unrequested label in P&L!A13 ('Esc. %'), and the all-or-nothing verifier fails any run that follows the instructions
  - Change: gt_18_RoadAssets_golden.xlsx P&L!A13: removed the unrequested label 'Esc. %' (cell now empty, style kept; it is blank in the input), no other cell changed. A13 is now a regression cell, so runs that leave it blank pass. Local verifier grade: new GT 1.0/1.0, and the old GT (with the label) still passes as an output under the 99.8% regression allowance.
- [F1](../findings.json) (Verification): Verifier requires an unrequested label restoration
  - Change: Same GT edit (P&L!A13 'Esc. %' removed).
- other finding, major, not in findings.json: Debt/Equity for FY37 is hardcoded 'NM' in the GT while Bank Loan is positive, and the rule-based formula the prompt describes is rejected
  - Change: answer_position: 'Ratio Analysis'!B2:T19 split into B2:T6, B7:Q7, S7:T7, B8:T19 so the ambiguous cell R7 (NM vs the formula's 1.1e-5) is no longer compared; N7:Q7 and S7:T7 stay graded. Grader guidance updated with the new ranges. Local SB2 scorer: GT 1.0, GT with R7 as the extended formula 1.0 (was FAIL), untouched input FAIL (mod 0.0).
