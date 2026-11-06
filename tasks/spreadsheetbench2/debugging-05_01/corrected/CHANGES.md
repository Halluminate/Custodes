# Changes: SpreadsheetBench 2 debugging-05_01

Fix summary (from the fix record):

The answer key's Total Current Assets and Total Current Liabilities still summed a days ratio (row 52) and a percentage (row 62) into dollar totals, which the audit prompt asks the agent to fix. Both totals now sum only the dollar lines, and working capital was recomputed. Checked locally: the patched key scores 1.0 against itself and the input with all key fixes applied scores 1.0.

Changed files (in this folder):

- reference/gt_05_golden.xlsx

## Fixed

- [F3](../findings.json) (Verification): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check falsely fails all 3 units (score 0.0) due to flawed ground truth in Model!E59:N59 and Model!E67:N67
  - Change: files/gt/gt_05_golden.xlsx: Model!E59:N59 '=SUM(x51:x53,x55,x57)' -> '=SUM(x51,x53,x55,x57)' (drops row 52 Days Unbilled Outstanding) and Model!E67:N67 '=SUM(x61:x63,x65)' -> '=SUM(x61,x63,x65)' (drops row 62 Net Revenue %). Cached values recomputed in LibreOffice for rows 59, 67, 68 and F69:H69 (e.g. E59 245.12 -> 137.738). No other cell changed.
- [F2](../findings.json) (Verification): Ground truth workbook gt_05_golden.xlsx retains invalid range sums in Model!E59:N59 and Model!E67:N67 that include Days Unbilled Outstanding (row 52) and Net Revenue % (row 62) in dollar totals
  - Change: Same GT change as verifier-correctness-0 (rows 59 and 67 sum only dollar lines, dependents recomputed).
- [F1](../findings.json) (Verification): Golden workbook retains invalid balance-sheet totals and penalizes their correction
  - Change: Same GT change as verifier-correctness-0 (rows 59 and 67 sum only dollar lines, dependents recomputed).
