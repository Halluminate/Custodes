# Changes: SpreadsheetBench 2 template-02_04

Fix summary (from the fix record):

Full pass: one prompt sentence says the per-quarter rates in rows 12 and 19 apply as given, the convention the key uses.

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, major, not in findings.json: Answer key applies an annual interest rate to quarterly periods without dividing by 4
  - Change: prompt.md: added after the instruction: 'Apply the interest rate shown for each quarter in rows 12 and 19 to that quarter's average balance as given, without converting it from an annual rate.' This states the key's convention (B13 = B12*AVERAGE(B9,B11) = 210.8); the answer key is unchanged.
- other finding, major, not in findings.json: Quarterly interest calculation depends on an unstated rate convention
  - Change: prompt.md: added after the instruction: 'Apply the interest rate shown for each quarter in rows 12 and 19 to that quarter's average balance as given, without converting it from an annual rate.' This states the key's convention (B13 = B12*AVERAGE(B9,B11) = 210.8); the answer key is unchanged.
