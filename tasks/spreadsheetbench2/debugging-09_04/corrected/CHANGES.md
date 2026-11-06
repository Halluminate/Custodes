# Changes: SpreadsheetBench 2 debugging-09_04

Fix summary (from the fix record):

Converged the circular LBO model's cached values in the golden and reference workbooks, and left the 289 circular LBO cells that do not settle in one LibreOffice recalculation out of answer_position, so the golden passes its own check whether the output keeps cached values or is saved with openpyxl. The key also fixes the extra colour slips QA named, and cells with no single correct colour are not compared.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_09_golden.xlsx
- reference/untouched_input_Inconsistent Color Coding_input.xlsx

## Fixed

- [F5](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells scores 0.0 on all units (and on gt_09_golden.xlsx itself) due to unconverged circular-reference cache mismatch and unfixed color-coding inconsistencies in ground truth
  - Change: Replaced gt_09_golden.xlsx and the untouched reference with copies recalculated in LibreOffice until the circular LBO debt schedule converged (six passes, last pass changes <1e-5). Formulas and font colors are unchanged (0 font differences). The modification set is now just the 38 font-color cells, and the golden grades 1.0 locally (regression 1.0, modification 1.0). The circular cells that do not settle in one recalculation are left out of answer_position (see F2). Not changed: valid extra fixes beyond the golden's 38 cells still count as regression errors under the benchmark's 99.8% rule.
- [F4](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: Replaced gt_09_golden.xlsx and the untouched reference with copies recalculated in LibreOffice until the circular LBO debt schedule converged (six passes, last pass changes <1e-5). Formulas and font colors are unchanged (0 font differences). The modification set is now just the 38 font-color cells, and the golden grades 1.0 locally (regression 1.0, modification 1.0). The circular cells that do not settle in one recalculation are left out of answer_position (see F2).
- [F3](../findings.json) (Reward): Ground truth workbook has unconverged circular-reference cached values and fails its own verifier upon LibreOffice recalculation (invalid_golden_solution)
  - Change: Replaced gt_09_golden.xlsx and the untouched reference with copies recalculated in LibreOffice until the circular LBO debt schedule converged (six passes, last pass changes <1e-5). Formulas and font colors are unchanged (0 font differences). The modification set is now just the 38 font-color cells, and the golden grades 1.0 locally (regression 1.0, modification 1.0). The circular cells that do not settle in one recalculation are left out of answer_position (see F2).
- [F1](../findings.json) (Reward): Golden workbook fails its own mandatory recalculation-based grading
  - Change: Replaced gt_09_golden.xlsx and the untouched reference with copies recalculated in LibreOffice until the circular LBO debt schedule converged (six passes, last pass changes <1e-5). Formulas and font colors are unchanged (0 font differences). The modification set is now just the 38 font-color cells, and the golden grades 1.0 locally (regression 1.0, modification 1.0). The circular cells that do not settle in one recalculation are left out of answer_position (see F2).
- [F2](../findings.json) (Reward): The circular model's forced LibreOffice recalculation makes the verifier fail correct outputs: the ground-truth workbook fails its own verifier, and a perfect color fix saved with openpyxl scores 0
  - Change: Golden and untouched reference recalculated in LibreOffice until the circular LBO debt schedule converged (formulas and font colours unchanged). The 289 LBO cells of the circular revolver/interest loop that do not settle in one LibreOffice recalculation (cold start from an openpyxl save, or warm start from the input's unconverged caches) are left out of answer_position and the guidance range text. Real SB2 scorer: golden 1.0, golden re-saved with openpyxl 1.0, untouched input fails (mod 0.0). No colour-fix cell is among the dropped cells.
- other finding, major, not in findings.json: Generic audit prompt and partially fixed ground truth leave target scope ambiguous and penalize valid fixes (mapping_ambiguity / undisclosed_constraints)
  - Change: gt_09_golden.xlsx (XML level, cloned font/xf entries; no other cell or style touched): LBO!D14, D15, D17, D18, D19, D21, D23, D24, D25, D27, H192 black -> blue 0000FF (hardcoded inputs, like the key's own D9); LBO!H59:N59 (=$N15) green -> black (same-sheet link); LBO!I6 black -> green 008000 (same INDEX link as Financials!H2, which is green); LBO!B17 =+B35&" Committment" -> =+B35&" Commitment" (cached 'Revolver Commitment'). answer_position split to skip cells with no single defensible colour: the 158 blue assumption formulas (LBO!D8, G91:N91, Financials J:N rows 10-28 and E17:F17, Operating Cases G13:N47 blue rows), LBO!F90 (pasted -5.293 that may instead become a formula) and the black cross-sheet label/date links (LBO!E47, B50, B52, Financials!B7, E7, Operating Cases!B7, E7, B9, B17, B25, B33, B41). graderGuidance range note updated. Local SB2 font_color scorer with recalc: new golden PASS, input + all 57 key changes PASS, untouched input FAIL (mod 0.0), old golden FAIL (20 errors).
- other finding, major, not in findings.json: Answer key applies the color convention inconsistently, so a thorough color audit is penalized
  - Change: Same GT recolouring and answer_position change as another finding (not listed).
