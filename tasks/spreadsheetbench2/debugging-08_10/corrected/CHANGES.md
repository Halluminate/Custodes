# Changes: SpreadsheetBench 2 debugging-08_10

Fix summary (from the fix record):

The prompt asks for a thorough audit, but the key fixed only the four planted unit mismatches and kept other real errors QA named. The key now also fixes them (R84, C90, C36:H36, K9:L9/K12/K15, M27, C111 discount exponent), recalculated with the verifier's LibreOffice. Cells with no single defensible repair (I62:L62, Comps + WACC C38, the two hardcoded sensitivity grids, Cover D8:D9) leave answer_position. The scope-limiting prompt sentence is removed.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_08_golden.xlsx

## Fixed

- [F5](../findings.json) (Verification): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells scores 0.0 on all 3 units because agents fix genuine workbook bugs alongside the 4 unit mismatches
  - Change: gt_08_golden.xlsx now also fixes the errors QA named, on top of the four planted unit mismatches, with every other cell, formula and style unchanged and 37 dependent cached values rewritten from the verifier's own LibreOffice recalc: 'Operating Model + DCF'!R84 =R847-M83 -> =R83-M83 (2026 change in NWC -113.91); C90 -0.3 -> 0.3 like D90:H90; C36:H36 ='IS Annual'!C75:H75 (empty) -> =CFS!E4:J4 (FY2019-FY2024 D&A, matched by year); K9:L9, K12, K15 (links to empty rows 41/47/53, the cells the findings name) -> =K8/K4, =L8/L4, =K11/K4, =K14/K4 like I:J; M27 divides by revenue M4 instead of COGS M7; C111 terminal value discounted ^5 -> ^6 to match H97 = 6 and H99 (C125 and C138 are not named and stay unchanged). Left out of answer_position because there is no single defensible repair: quarterly capex I62:L62 (point at the depreciation row; the workbook has no quarterly capex), 'Comps + WACC'!C38 (WACC = cost of equity; a weighted WACC needs a choice of debt and equity weights; nothing references C38), the hardcoded sensitivity grids G108:K112 and G122:K126 (they are stale against the corrected DCF and can be rebuilt several ways) and the blank Cover!D8:D9 target price/upside (no method is specified). Checked with the real SB2 scorer: new key vs itself 1.0; untouched input plus all key fixes 1.0; untouched input 0.0 (mod 0.0); planted-only fixes (the old key) now fail (mod 0.6848), as expected.
- [F2](../findings.json) (Verification): Golden workbook (gt_08_golden.xlsx) leaves broken cell references, formula logic errors, and sign errors unfixed that cascade into graded cells
  - Change: Same key change: R84, C90, M27, C36:H36, K9:L9/K12/K15 fixed in the key; I62:L62 out of answer_position.
- [F3](../findings.json) (Task Spec): Task prompt instructs a comprehensive workbook audit while the verifier enforces an undisclosed constraint to only fix four unit-mismatch items
  - Change: Same key change (R84, C36:H36, K9:L9 fixed). The hardcoded sensitivity grids G108:K112, G122:K126 and the blank Cover!D8:D9 leave answer_position (no single defensible repair). The prompt keeps its original 'audit and fix thoroughly' text; the earlier scope sentence was removed.
- [F4](../findings.json) (Verification): Fixing a real error the answer key leaves in place fails the all-or-nothing verifier
  - Change: Same key change: C90 -> 0.3 and C111 discounted ^6; 'Comps + WACC'!C38 leaves answer_position (no single defensible WACC weighting).
- [F1](../findings.json) (Verification): Ground truth penalizes correcting a broken working-capital reference
  - Change: Same key change: R84 -> =R83-M83 with D94, D95, D100, C102 and the DCF blocks recalculated.
