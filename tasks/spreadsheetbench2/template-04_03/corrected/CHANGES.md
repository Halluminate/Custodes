# Changes: SpreadsheetBench 2 template-04_03

Fix summary (from the fix record):

The answer key mixed two depreciation conventions (2026-2027 used the previous column's beginning PP&E, 2028 the same column's) and its 2028 FCF did not sum its own lines. Depreciation is now the rate times the same year's beginning PP&E (as in the history and the G33 formula), with the PP&E roll-forward and FCF totals recomputed. Full pass: historical cells the key leaves blank are no longer graded, so filling them is not penalized.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_04_03_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check fails valid financial models due to buggy ground truth values in E33 and F33
  - Change: gt_04_03_golden.xlsx FCF_Calculation: E33 8.1305 -> 8.441 (=E17*E15), F33 8.808 -> 9.10021 (=F17*F15), G33 cached 9.29129 -> 9.21897 (formula =G17*G15 kept); F15 76.14559 -> 75.83509 and G15 77.42742 -> 76.82471 rolled forward with the corrected depreciation; E39:G39 recomputed as SUM(32:38) = 33.42135, 34.61072, 35.14904.
- [F3](../findings.json) (Verification): Invalid golden solution and ambiguous 'Prior Year PP&E' definition cause 2026–2028 PP&E and Depreciation cells to contradict standard accounting and row labels
  - Change: Same GT patch: one depreciation convention for 2026-2028 matching the 2024-2025 roll-forward, and G39 now equals the sum of G32:G38. D15/E15 kept (differences of about 0.0002 are far inside the 1% tolerance).
- [F2](../findings.json) (Verification): Ground-truth depreciation formula is inconsistent across 2026–2028, and every consistent method fails the binary check
  - Change: Same GT patch; a model built consistently with =E17*E15 style formulas now scores regression 1.0, modification 1.0 locally (old GT failed on E33/F33).
- [F1](../findings.json) (Verification): Incorrect 2028 depreciation in the answer key causes consistent models to fail
  - Change: Same GT patch; G33 and G39 now agree with each other and with the same-column convention.
- other finding, major, not in findings.json: Undisclosed constraint on leaving historical ratio cells (C20:D20, C23:D23, C26:D26) blank despite C16:D17 being populated
  - Change: verifications[0].parameters.answer_position: 'FCF_Calculation'!B2:G48 split to skip the historical 2024-2025 cells the key leaves blank but an analyst may fairly fill: growth/margin C9:D10, OWC/Other LT Liab./Other LT Assets ratios C20:D20, C23:D23, C26:D26 and the historical FCF block C32:D39. All key (modification) cells stay graded. Grader guidance updated. SB2 scorer: patched golden 1.0; golden with those historical cells filled 1.0 (was reg 0.9498 FAIL); untouched input fails (mod 0).
- other finding, major, not in findings.json: Vague 'complete the model' prompt, but filling any reasonable extra cell fails the all-or-nothing check
  - Change: Same answer_position change (C9:D10 and C32:D39 included).
