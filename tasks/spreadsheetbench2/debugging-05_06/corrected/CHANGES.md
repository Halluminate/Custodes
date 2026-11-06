# Changes: SpreadsheetBench 2 debugging-05_06

Fix summary (from the fix record):

The golden kept working-capital subtotals that add Days Unbilled Outstanding and a revenue % to dollar balances; the key now sums only the dollar lines.

Changed files (in this folder):

- reference/gt_05_golden.xlsx

## Fixed

- other finding, major, not in findings.json: Golden workbook penalizes correct repairs to broken working-capital subtotals
  - Change: gt_05_golden.xlsx Model!E59:N59 '=SUM(E51:E53,E55,E57)' -> '=SUM(E51,E53,E55,E57)' and E67:N67 '=SUM(E61:E63,E65)' -> '=SUM(E61,E63,E65)' (drop row 52 Days Unbilled Outstanding and row 62 Net Revenue %). Cached values recomputed with the verifier's LibreOffice recalc; only the 33 cells that depend on them changed (rows 59, 67, 68 and F69:H69; projected deltas cancel so nothing further moves). answer_position unchanged. Local SB2 scorer: patched golden PASS (reg 1.0, mod 1.0); input + the 4 planted fixes + the subtotal fixes PASS; input + only the 4 planted fixes FAIL (mod 0.9091, the 23 subtotal-dependent cells); untouched input FAIL (mod 0.0).
