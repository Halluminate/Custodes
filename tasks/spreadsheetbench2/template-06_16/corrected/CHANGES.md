# Changes: SpreadsheetBench 2 template-06_16

Fix summary (from the fix record):

The answer key left the labelled 'YoY Growth %' row blank for Q1-Q3 2007 although the 2006 comparables exist, so completing it failed the regression check. The answer key now fills H10:J10 with the YoY formulas.

Changed files (in this folder):

- reference/gt_06_16_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check returns false negative (score 0.0) on all 3 units due to H10:J10 YoY Growth %
  - Change: gt_06_16_golden.xlsx, QuarterlyPL_Forecast: added H10 =(H8/C8)-1, I10 =(I8/D8)-1, J10 =(J8/E8)-1 (21.14%, 16.11%, 11.49%) with the QoQ row's 0.00% style. H10:J10 are now modification cells, so completing the labelled row no longer fails the regression ratio. No other cell changed. The patched GT scores 1.0 on the local SB2 cell check.
- [F3](../findings.json) (Verification): Golden workbook leaves Q1-Q3 2007 YoY Growth % (H10:J10) blank, penalizing complete solutions as regression errors
  - Change: Same answer-key fix as verifier-correctness-0 (GT QuarterlyPL_Forecast!H10:J10 filled with YoY formulas).
- [F1](../findings.json) (Verification): The labelled 'YoY Growth %' row is left blank in the ground truth, and filling it fails the whole task
  - Change: Same answer-key fix as verifier-correctness-0 (GT QuarterlyPL_Forecast!H10:J10 filled with YoY formulas).
- [F2](../findings.json) (Verification): Completing the labeled YoY growth row causes the entire task to fail grading
  - Change: Same answer-key fix as verifier-correctness-0 (GT QuarterlyPL_Forecast!H10:J10 filled with YoY formulas).
