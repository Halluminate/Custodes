# Changes: SpreadsheetBench 2 financial-model-18_02

Fix summary (from the fix record):

The answer key had an unrequested 'Esc. %' label in P&L!A13 and hardcoded 'NM' in Ratio Analysis!R19:T19 although EBITDA is positive. Removed the label and extended the row's IF formula to R19:T19.

Changed files (in this folder):

- reference/gt_18_RoadAssets_golden.xlsx

## Fixed

- [F7](../findings.json) (Verification): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check gives false-negative 0.0 scores to units 2 and 3 due to defective ground-truth cells P&L!A13 and Ratio Analysis!R19:T19
  - Change: gt_18_RoadAssets_golden.xlsx: P&L!A13 cleared (was 'Esc. %'), Ratio Analysis!R19:T19 set to =IF(R10<=0,"NM",R6/R10) etc. (values 4.54e-05, 0, 0), recalculated in LibreOffice. No other cell changed.
- [F3](../findings.json) (Task Spec): Verifier enforces an undisclosed modification at P&L!A13 ('Esc. %') that is never mentioned in the instructions
  - Change: gt_18_RoadAssets_golden.xlsx: P&L!A13 cleared to match the input.
- [F5](../findings.json) (Verification): Golden workbook hardcodes 'NM' in Ratio Analysis!R19:T19 despite positive EBITDA, contradicting the prompt and existing formula pattern
  - Change: gt_18_RoadAssets_golden.xlsx: Ratio Analysis!R19:T19 now =IF(x10<=0,"NM",x6/x10) like N19:Q19.
- [F1](../findings.json) (Verification): Answer key puts 'NM' in Total Debt/EBITDA for FY37–FY39 even though EBITDA is positive, so following the instruction fails the task
  - Change: Same GT edit as F5: Ratio Analysis!R19:T19 formulas replace hardcoded 'NM'.
- [F6](../findings.json) (Verification): Answer key requires a label in P&L!A13 ('Esc. %') that the instruction never asks for
  - Change: Same GT edit as F3: P&L!A13 cleared.

## Confirmed findings not fixed

- [F4](../findings.json): Golden debt-to-EBITDA answers contradict the required NM rule
  - Reason: duplicate-of:F5
- [F2](../findings.json): Verifier requires an unrequested P&L label
  - Reason: duplicate-of:F3
