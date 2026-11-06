# Changes: SpreadsheetBench 2 debugging-05_05

Changed files (in this folder):

- reference/gt_05_golden.xlsx

## Fixed

- other finding, major, not in findings.json: Answer key penalizes correcting invalid working-capital totals
  - Change: gt_05_golden.xlsx (XML edits, dependents recached from the verifier's LibreOffice recalc, nothing else changed): Model!E59:N59 =SUM(x51:x53,x55,x57) -> =SUM(x51,x53,x55,x57) (drops row 52 Days Unbilled Outstanding) and E67:N67 =SUM(x61:x63,x65) -> =SUM(x61,x63,x65) (drops row 62 Net Revenue %). Recached: rows 59, 67, 68 (E:N) and F69:H69; projected days and % are flat, so I69:N69 and the cash flow/debt block do not move. Scorer: new key 1.0 vs itself; previous key now fails; untouched input fails.
