# Changes: SpreadsheetBench 2 debugging-05_08

Fix summary (from the fix record):

The answer key now fixes the two Balance Sheet subtotal bugs QA named (current assets summing a days row, current liabilities summing a ratio row), with working capital and its changes recomputed. The earlier fix that stopped grading those cells is reverted, so the original grading range is used.

Changed files (in this folder):

- reference/gt_05_golden.xlsx

## Fixed

- [F3](../findings.json) (Verification): SpreadsheetBench 2 official cell check: False negative on unit 1 due to unfixed Balance Sheet SUM bugs in gt_05_golden.xlsx
  - Change: files/gt/gt_05_golden.xlsx (new): Model!E59:N59 '=SUM(E51:E53,E55,E57)' -> '=SUM(E51,E53,E55,E57)' (Total Current Assets no longer adds row 52 Days Unbilled Outstanding) and E67:N67 '=SUM(E61:E63,E65)' -> '=SUM(E61,E63,E65)' (Total Current Liabilities no longer adds row 62 Net Revenue %). 33 cached values recomputed with the verifier's LibreOffice recalc (E59 245.12 -> 137.74, E68 159.20 -> 51.89, F69 -28.52 -> -2.07). The earlier answer_position cut-out of these cells is reverted: the original verifier parameters are kept and the cells are graded against the corrected values.
- [F1](../findings.json) (Verification): Golden workbook gt_05_golden.xlsx retains unfixed Balance Sheet SUM formula bugs while the prompt instructs a general audit, penalizing agents that fix non-INDEX/MATCH errors
  - Change: files/gt/gt_05_golden.xlsx (new): Model!E59:N59 '=SUM(E51:E53,E55,E57)' -> '=SUM(E51,E53,E55,E57)' (Total Current Assets no longer adds row 52 Days Unbilled Outstanding) and E67:N67 '=SUM(E61:E63,E65)' -> '=SUM(E61,E63,E65)' (Total Current Liabilities no longer adds row 62 Net Revenue %). 33 cached values recomputed with the verifier's LibreOffice recalc (E59 245.12 -> 137.74, E68 159.20 -> 51.89, F69 -28.52 -> -2.07). The earlier answer_position cut-out of these cells is reverted: the original verifier parameters are kept and the cells are graded against the corrected values.
- [F2](../findings.json) (Verification): Answer key penalizes correcting materially incorrect balance-sheet totals
  - Change: files/gt/gt_05_golden.xlsx (new): Model!E59:N59 '=SUM(E51:E53,E55,E57)' -> '=SUM(E51,E53,E55,E57)' (Total Current Assets no longer adds row 52 Days Unbilled Outstanding) and E67:N67 '=SUM(E61:E63,E65)' -> '=SUM(E61,E63,E65)' (Total Current Liabilities no longer adds row 62 Net Revenue %). 33 cached values recomputed with the verifier's LibreOffice recalc (E59 245.12 -> 137.74, E68 159.20 -> 51.89, F69 -28.52 -> -2.07). The earlier answer_position cut-out of these cells is reverted: the original verifier parameters are kept and the cells are graded against the corrected values.
