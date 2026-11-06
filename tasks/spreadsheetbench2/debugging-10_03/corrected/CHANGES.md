# Changes: SpreadsheetBench 2 debugging-10_03

Fix summary (from the fix record):

The unconverged circular revolver/interest block is no longer graded, so the golden passes its own check. Full pass: the key's hardcoded Model!H43 is now =SUM($F43,G43) with its dependents' cached values, and the undisclosed 'Total Sales' label and four float-residue cells are no longer graded.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_10_golden.xlsx

## Fixed

- other finding, major, not in findings.json: Undisclosed exact label 'Total Sales' required at deleted cell Model!B48 while summary sheets call the same line 'Total Revenue'
  - Change: verifications[0].parameters.answer_position: 'Model'!B2:AX335 split into B2:AX47, C48:AX48, B49:AX335, leaving out only the restored row's label cell Model!B48 (the row's formulas C48:AX48 and the shifted rows are still graded). Mode, id, name, function, weight unchanged; graderGuidance range text updated.
- other finding, major, not in findings.json: The prompt asks for a broad audit (fix hardcodes and best-practice issues), but the answer key keeps obvious hardcodes, so fixing them can fail the all-or-nothing grade
  - Change: gt_10_golden.xlsx (XML edits on the original key): Model!H43 0.1 -> =SUM($F43,G43) (0.19736124). Cached values of the 53 cells whose value then moves beyond the 1% tolerance were taken from the verifier's LibreOffice recalc of the patched key (recalc of the original key from the same caches used as the baseline): Model H44, H46, H49, I43:M43, X20, X26 and the cash-sweep cells I195, J119, J120, J130, J132, J137, J138, J190, K137, K138, L122:L124, L126, L127, L137, L138, L141; 'P&L Summary' F8, F9, G8:K8, F11, F14, F36, F37, H38:J39, N32, N34, N38, O32, O34, Q18, Q33, Q37. No other cell changed. Local SB2 grade: the previous key as output now fails on H43 and these dependents; the new key against itself fails only on the pre-existing unconverged circular cells (245 errors, was 251; verifier-correctness-0, not fixable).
- other finding, minor, not in findings.json: Floating-point rounding residue (around 1e-16) is counted as required changes on 4-Wall Analysis
  - Change: verifications[0].parameters.answer_position: '4-Wall Analysis'!A2:DX1443 split to leave out the four zero-check cells AR867, AR939, BE1083, BE1155 (float residues); graderGuidance range text updated.
- [F4](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells is a trivial-fail verifier (scores 0.0 even on gt_10_golden.xlsx itself) due to a non-convergent circular reference in Model!I195:M195 during LibreOffice recalculation
  - Change: Cleanup (rule 5): the 187 circular revolver/interest cells and their direct dependents that do not settle under one LibreOffice recalc are left out of answer_position and the guidance range text (Model I:M rows 121-124, 126-127, 141, 146-147, 180-183, 186-190, 193-199; Model R:T and AL:AN rows 24-25, 27-28, 30-31; Model AW20:AW23, AW37, AW39:AW41; Model X20, X26; 'P&L Summary' G40:K41 and R7:T8), the same block as sibling 10_04 (<id>). Real SB2 scorer: new golden PASS reg 1.0 mod 1.0 (was mod 0.9817, 161 modification errors, all in this block); untouched input FAIL mod 0.0.

## Confirmed findings not fixed

- [F3](../findings.json): Golden gate: the ground-truth deliverable does not score full reward
  - Reason: duplicate-of:verifier-correctness-0
- [F1](../findings.json): The answer key fails its own verifier after the LibreOffice recalculation the verifier applies, so the task cannot be passed
  - Reason: duplicate-of:verifier-correctness-0
- [F2](../findings.json): Golden workbook fails its own verifier after required recalculation
  - Reason: duplicate-of:verifier-correctness-0
