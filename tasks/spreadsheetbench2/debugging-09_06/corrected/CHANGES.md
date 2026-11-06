# Changes: SpreadsheetBench 2 debugging-09_06

Fix summary (from the fix record):

The model is circular and LibreOffice needs about ten passes to converge it, so the golden caches (one unconverged pass) and any agent output graded after one pass never agreed. The key and reference now hold converged caches, and the loop cells whose values depend on the number of recalculation passes are left out of the compared range. Golden, and the exact fix saved after 0, 1 or 2 extra recalcs, all pass; the untouched input still fails.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_09_golden.xlsx
- reference/untouched_input_Incorrect Cross Sheet References_input.xlsx

## Fixed

- [F4](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: ground_truth/gt_09_golden.xlsx and untouched_input_Incorrect Cross Sheet References_input.xlsx: cached <v> of the 257 / 259 circular-loop cells on LBO replaced with their converged values (each workbook's own formulas run through the verifier's recalculation until no value moved, 10-12 passes); formulas, styles and every other cell unchanged (LBO!D8 =TODAY() left as is). verifications[0].parameters.answer_position: 'LBO'!A2:X218 replaced by 79 sub-ranges that skip the 294 LBO cells inside the iterative interest/revolver/cash-sweep loop (rows 67-205 cols G:N where they move between LibreOffice passes, plus D213/L213 labels); the four fixed reference rows (G51:N51, G63:N63, E87:F87) and all non-loop cells stay graded, Financials and Operating Cases unchanged. The verifier's single LibreOffice pass does not converge this loop, so these cells depended on how many times the agent had recalculated. Local replay: new and old golden PASS.
- [F5](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells gives false-negative 0.0 verdicts on exact formula fixes due to unconverged circular references in gt_09_golden.xlsx
  - Change: Same GT/reference re-cache and answer_position change; the exact four reference fixes saved with openpyxl (no recalc) or after 1 or 2 LibreOffice recalcs now PASS (were mod 0.50 / 0.59 / 0.93 FAIL).
- [F3](../findings.json) (Reward): Unconverged circular-reference cached values in ground truth cause valid solutions (and the golden workbook itself) to fail value verification
  - Change: Same as gt-replay-0.
- [F1](../findings.json) (Reward): Ground-truth workbook fails its own grading: unconverged circular values make the official check unpassable
  - Change: Same as gt-replay-0.
- [F2](../findings.json) (Reward): Golden workbook fails its own verifier after mandatory recalculation
  - Change: Same as gt-replay-0.
