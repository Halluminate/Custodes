# Changes: SpreadsheetBench 2 debugging-05_10

Fix summary (from the fix record):

The answer key kept two unit-mismatch errors from the original model: Total Current Assets added a days metric and Total Current Liabilities added a percentage. Both totals now sum only the dollar balances, so a thorough unit audit is no longer marked wrong.

Changed files (in this folder):

- reference/gt_05_golden.xlsx

## Fixed

- [F1](../findings.json) (Verification): Golden workbook requires retaining dimensionally invalid balance-sheet totals
  - Change: gt_05_golden.xlsx, Model: Total Current Assets E59:N59 changed from =SUM(x51:x53,x55,x57) to =SUM(x51,x53,x55,x57), dropping row 52 'Days Unbilled Outstanding' (days). Total Current Liabilities E67:N67 changed from =SUM(x61:x63,x65) to =SUM(x61,x63,x65), dropping row 62 'Net Revenue %'. Cached values recomputed with the verifier's LibreOffice recalc: 33 cells change (rows 59, 67, 68 Working Capital, 69 Change, e.g. E59 245.12 -> 137.74). Rows 87 onward are unchanged because the forecast-year change in working capital is the same with or without the stray items. Only these formulas and <v> caches were patched. The patched GT and a cache-free copy both score 1.0 locally. Rechecked in the audit rework (no further key change needed, the finding names only these two totals): new key vs itself 1.0, input plus all key fixes 1.0, untouched input 0.0, planted-only fixes (original key) 0.0 (expected).
