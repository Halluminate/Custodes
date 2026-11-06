# Changes: SpreadsheetBench 2 debugging-05_03

Changed files (in this folder):

- reference/gt_05_golden.xlsx

## Fixed

- other finding, major, not in findings.json: Answer key retains incorrect balance-sheet totals and penalizes valid audit fixes
  - Change: gt_05_golden.xlsx (XML-level): Model!E59:N59 =SUM(x51:x53,x55,x57) -> =SUM(x51,x53,x55,x57) and E67:N67 =SUM(x61:x63,x65) -> =SUM(x61,x63,x65); cached values refreshed by one verifier LibreOffice recalc only where they changed: rows 59, 67, 68 (E:N) and F69:H69 (33 cells); no other cell moved. answer_position unchanged. Real scorer: patched golden PASS (reg 1.0, mod 1.0); untouched input FAIL (mod 0.0).
