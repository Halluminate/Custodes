# Changes: SpreadsheetBench 2 template-16_06

Fix summary (from the fix record):

The answer key's Total Other Income (Valuation!D23) summed the per-SF column C23:C26 instead of the annual amounts. It now sums D19:D22, and the downstream cached values were recalculated.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_16_06_golden.xlsx

## Fixed

- [F3](../findings.json) (Verification): Golden workbook has a wrong formula in Valuation!D23 (=SUM(C23:C26) instead of =SUM(D19:D22)), corrupting 11 downstream cells
  - Change: gt_16_06_golden.xlsx: Valuation!D23 changed from =SUM(C23:C26) to =SUM(D19:D22) (1,048,642). Recalculated the workbook so the 13 downstream cells (C25:D26, C28:D28, C42:D42, C44:D44, C46:D46, D50) hold the corrected values. No other cell changed. The patched GT scores 1.0 on the local SB2 cell check.
- [F2](../findings.json) (Verification): Ground-truth Total Other Income (Valuation!D23) adds the wrong column and creates a circular reference, so every figure below it is wrong
  - Change: gt_16_06_golden.xlsx: Valuation!D23 changed from =SUM(C23:C26) to =SUM(D19:D22) (1,048,642). Recalculated the workbook so the 13 downstream cells (C25:D26, C28:D28, C42:D42, C44:D44, C46:D46, D50) hold the corrected values. No other cell changed. The patched GT scores 1.0 on the local SB2 cell check.
- [F1](../findings.json) (Verification): Answer key uses an incorrect, circular other-income subtotal
  - Change: gt_16_06_golden.xlsx: Valuation!D23 changed from =SUM(C23:C26) to =SUM(D19:D22) (1,048,642). Recalculated the workbook so the 13 downstream cells (C25:D26, C28:D28, C42:D42, C44:D44, C46:D46, D50) hold the corrected values. No other cell changed. The patched GT scores 1.0 on the local SB2 cell check.
- other finding, major, not in findings.json: Ground truth puts NOI margin (%) in a column headed '$/Unit/Yr', so the per-unit NOI an agent would naturally enter fails
  - Change: verifications[0].parameters.answer_position: Valuation!B2:E50 split to skip C46 (key =D46/D28 NOI margin; the column header says $/Unit/Yr, so D46/C6 is equally defensible). graderGuidance range note updated. Local SB2 scorer with recalc: golden PASS, input + key changes PASS, input + key with C46 = D46/C6 PASS, untouched input FAIL (mod 0.0).
- other finding, major, not in findings.json: Seed rent roll stores numbers as text, and fixing them is penalised by the regression check
  - Change: verifications[0].parameters.answer_position: RentRoll!B2:P18 split to skip the text-stored inputs F9, F11, F12, H8:H12, K8:K12 and the SUMPRODUCT totals F13 and H13 that they break, so keeping them as given or converting them to numbers both pass. graderGuidance range note updated. Local SB2 scorer: golden PASS, input + key changes PASS, the same with those 13 inputs converted to numbers PASS, untouched input FAIL.
