# Changes: SpreadsheetBench 2 financial-model-08_01

Fix summary (from the fix record):

Removed the unstated /12 from the answer key's 'NWC as % Revenue' row so it matches the instruction's monthly NWC-to-revenue ratio.

Changed files (in this folder):

- reference/gt_08_Seafood_golden.xlsx

## Fixed

- [F1](../findings.json) (Task Spec): Undisclosed division by 12 (annualization) in Working Capital 'NWC as % Revenue' ground truth
  - Change: gt_08_Seafood_golden.xlsx 'Working Capital'!J53:BV53 (65 cells): removed the trailing /12 from =IFERROR((J52/'Income Statement'!P6),"")/12 and set each cached value to J52/P6 (e.g. J53 0.1625 -> 1.9495), so the key computes NWC as a percentage of that month's revenue as the instruction says. Patched in the sheet XML only; local verifier on the patched golden: PASS, reg 1.0, mod 1.0.
- [F2](../findings.json) (Verification): Answer key silently annualizes the requested monthly NWC ratio
  - Change: Same J53:BV53 answer-key correction.
- [F3](../findings.json) (Task Spec): SpreadsheetBench 2 official cell check: All-or-nothing cell verifier trivially fails all runs due to unlinked hardcoded DCF sensitivity table values and undisclosed NWC/12 convention
  - Change: Same J53:BV53 correction (the confirmed part of this finding). The DCF sensitivity-table cells D28:I54 stay graded because the instruction asks for them.
