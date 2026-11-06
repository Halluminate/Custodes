# Changes: SpreadsheetBench 2 template-11_01

Fix summary (from the fix record):

The answer key showed a 14.29% Year 7 repayment rate next to a 100% balloon repayment. DebtSchedule!K8 in the key is now 100%, so a consistent model passes. The two tool findings are tool behaviour and left as infra.

Changed files (in this folder):

- reference/gt_11_01_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check fails all three valid attempts (score 0.0) due to defective ground truth at DebtSchedule!K8
  - Change: gt_11_01_golden.xlsx: DebtSchedule!K8 (Year 7 scheduled repayment %) changed from =1/$D$19 (14.29%) to 1 (100%), matching the D22 balloon assumption and K9 = K7. No other cell value, formula or format changed (checked after LibreOffice recalculation).
- [F3](../findings.json) (Verification): Golden ground-truth workbook has an erroneous formula in DebtSchedule!K8 that contradicts the Year 7 balloon repayment assumption in D22
  - Change: gt_11_01_golden.xlsx: DebtSchedule!K8 (Year 7 scheduled repayment %) changed from =1/$D$19 (14.29%) to 1 (100%), matching the D22 balloon assumption and K9 = K7. No other cell value, formula or format changed (checked after LibreOffice recalculation).
- [F2](../findings.json) (Verification): Answer key shows a 14.29% Year 7 repayment rate next to a 100% balloon repayment, so a consistent 100% entry fails the all-or-nothing check
  - Change: gt_11_01_golden.xlsx: DebtSchedule!K8 (Year 7 scheduled repayment %) changed from =1/$D$19 (14.29%) to 1 (100%), matching the D22 balloon assumption and K9 = K7. No other cell value, formula or format changed (checked after LibreOffice recalculation).
- [F1](../findings.json) (Verification): Answer key requires an inconsistent Year 7 repayment percentage
  - Change: gt_11_01_golden.xlsx: DebtSchedule!K8 (Year 7 scheduled repayment %) changed from =1/$D$19 (14.29%) to 1 (100%), matching the D22 balloon assumption and K9 = K7. No other cell value, formula or format changed (checked after LibreOffice recalculation).
