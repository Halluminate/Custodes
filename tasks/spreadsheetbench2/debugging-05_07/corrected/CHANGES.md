# Changes: SpreadsheetBench 2 debugging-05_07

Fix summary (from the fix record):

The input had overwritten the 2019-2021 Gross Profit cost constants with a copy of C16's +179.281, so the answer key's -308.126/-261.587/-217.881 could not be derived. The input now holds those constants with the injected wrong sign, so a sign fix recovers the answer key. Full pass: the answer key also fixes the Total Current Assets / Total Current Liabilities sums that added a days row and a % row (Model E59:N59, E67:N67).

Changed files (in this folder):

- reference/untouched_input_Incorrect Sign Conventions_input.xlsx
- reference/gt_05_golden.xlsx
- inputs/Incorrect Sign Conventions_input.xlsx

## Fixed

- [F4](../findings.json) (Environment & Infra): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check trivially fails all runs (0.0) because 22 modification cells depend on historical constants destroyed in the input file
  - Change: Input 'Financial Overview'!D16:F16 restored to the original per-year cost constants with the injected sign error kept: D16 =D8+308.126, E16 =E8+261.587, F16 =F8+217.881 (they had been overwritten with =X8+179.281 copied from C16). The cached values of these cells and their 22 dependents (Financial Overview D17:F18, K16 and Model C29:D34, P29, P31, P33) are set from a forced LibreOffice recalculation. The change is made in both 'Incorrect Sign Conventions_input.xlsx' (agent data) and 'untouched_input_Incorrect Sign Conventions_input.xlsx' (verifier reference). Nothing else changed. The GT is unchanged and still scores reg 1.0 / mod 1.0 against the new reference.
- [F1](../findings.json) (Environment & Infra): Input workbook destroyed hardcoded historical constants in Financial Overview!D16:F16 that the verifier requires to match gt_05_golden.xlsx
  - Change: Same input fix: D16 =D8+308.126, E16 =E8+261.587, F16 =F8+217.881 in the data file and in the untouched reference input.
- [F2](../findings.json) (Verification): Ground truth uses per-year Gross Profit constants for 2019 and 2020 that cannot be derived from anything in the input, so the binary verifier cannot be passed
  - Change: Same input fix: the per-year constants are now in the input with flipped signs, so the GT's =D8-308.126 etc. is a pure sign correction.
- [F3](../findings.json) (Environment & Infra): Historical cost data needed for two graded corrections is missing
  - Change: Same input fix: the 2019/2020/2021 cost figures 308.126, 261.587 and 217.881 are now present in the input.
- other finding, major, not in findings.json: The answer key preserves invalid balance-sheet subtotals and rejects their repair
  - Change: files/gt/gt_05_golden.xlsx (new in the answer key): Model!E59:N59 =SUM(X51:X53,X55,X57) -> =SUM(X51,X53,X55,X57) (drops row 52, Days Unbilled Outstanding) and Model!E67:N67 =SUM(X61:X63,X65) -> =SUM(X61,X63,X65) (drops row 62, a Net Revenue %), so current assets and liabilities add only money rows (E59 245.121 -> 137.738, E68 159.203 -> 51.887). XML edits; cached values recomputed with the verifier's LibreOffice recalc and written only for the 33 cells whose recalculated value changed (rows 59, 67, 68 E:N and F69:H69; projected change rows I69:N69 are unchanged because days and % hold flat). Input files unchanged. Real scorer: new key 1.0 vs itself, current input + all key changes 1.0, untouched input 0 (mod 0.0), the previous key (sign fixes only) now fails (mod 0.8736).
