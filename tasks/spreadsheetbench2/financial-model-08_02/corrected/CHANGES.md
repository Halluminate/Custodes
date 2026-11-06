# Changes: SpreadsheetBench 2 financial-model-08_02

Fix summary (from the fix record):

Removed the unrequested DCF Valuation!D35 value from the golden. The circular capex and debt cells that settle at different values when a workbook is saved without cached values (as openpyxl does) are left out of the graded range, so the save tool no longer decides the grade.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_08_Seafood_golden.xlsx

## Fixed

- [F5](../findings.json) (Task Spec): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check fails all units (including Unit 3's complete solution) due to uninstructed modification cell DCF Valuation!D35 in ground truth
  - Change: Golden gt_08_Seafood_golden.xlsx: cleared the unrequested hardcoded 0.143833422543056 in 'DCF Valuation'!D35 (a direct XML edit, so no other cell or cached value changed). D35 now matches the input and counts as a regression cell. The patched golden grades 1.0 locally.
- [F2](../findings.json) (Verification): Undisclosed modification cell DCF Valuation!D35 in ground truth is blank in input workbook and never mentioned in instructions
  - Change: Golden gt_08_Seafood_golden.xlsx: cleared the unrequested hardcoded 0.143833422543056 in 'DCF Valuation'!D35 (a direct XML edit, so no other cell or cached value changed). D35 now matches the input and counts as a regression cell. The patched golden grades 1.0 locally.
- [F1](../findings.json) (Task Spec): Answer key requires an unrequested hardcoded value in DCF Valuation!D35, so no faithful solution can pass
  - Change: Golden gt_08_Seafood_golden.xlsx: cleared the unrequested hardcoded 0.143833422543056 in 'DCF Valuation'!D35 (a direct XML edit, so no other cell or cached value changed). D35 now matches the input and counts as a regression cell. The patched golden grades 1.0 locally.
- [F4](../findings.json) (Task Spec): Verifier requires an unrequested repair to DCF Valuation!D35
  - Change: Golden gt_08_Seafood_golden.xlsx: cleared the unrequested hardcoded 0.143833422543056 in 'DCF Valuation'!D35 (a direct XML edit, so no other cell or cached value changed). D35 now matches the input and counts as a regression cell. The patched golden grades 1.0 locally.
- [F3](../findings.json) (Reward): Using openpyxl as the prompt recommends shifts ~1,139 Capex-sheet values on recalculation, pushing regression below the 99.8% pass bar
  - Change: verifications[0].parameters.answer_position (+ graderGuidance range text): 'Capex and Debt Assumptions '!A2:DL319 split into 75 ranges that leave out the 1,139 cells of the circular capex and debt block (rows 155-185 and 214-319, columns C:R) that a LibreOffice recalculation from a workbook without cached values (as openpyxl saves it) settles at a different fixed point. All are regression cells. Real SB2 scorer with the new answer_position: golden PASS (reg 1.0, mod 1.0), the golden re-saved with openpyxl PASS (was reg 0.9939, 1,141 errors), untouched input FAIL (mod 0.0001). The prompt line naming a save method is removed.
