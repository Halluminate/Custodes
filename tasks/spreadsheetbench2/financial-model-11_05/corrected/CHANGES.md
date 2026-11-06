# Changes: SpreadsheetBench 2 financial-model-11_05

Fix summary (from the fix record):

The seeded BG!V32 (Mar-27 Periodic BG Requirements) used =U31+V31, a pattern that contradicts both the annual logic and the key's quarterly change formulas next to it. V32 is now =V31 in the input, the untouched reference and the golden, so the quarters reconcile to the annual J32.

Changed files (in this folder):

- reference/gt_11_Switchgear_golden.xlsx
- reference/untouched_input_11_05_Switchgear_input.xlsx
- inputs/11_05_Switchgear_input.xlsx

## Fixed

- other finding, major, not in findings.json: The seeded formula in the column right before the graded Periodic BG Requirements range follows a different, apparently wrong pattern
  - Change: BG!V32 formula =U31+V31 -> =V31 (mirrors annual J32 =J31; quarterly FY27 now equals annual -1.10538352 and FY28 quarters sum to K32). Applied at XML level to 11_05_Switchgear_input.xlsx (cached 0, upstream blank), untouched_input_11_05_Switchgear_input.xlsx (cached 0) and gt_11_Switchgear_golden.xlsx (cached -0.731294639999998 -> -1.10538352). No formula anywhere references BG row 32, so no other cell changes. SB2 scorer: golden 1.0, untouched input 0.0 (879 cell errors).
- other finding, major, not in findings.json: Pre-filled periodic BG formula uses addition instead of the subsequent periods' change convention
  - Change: Same BG!V32 fix as another finding (not listed).
