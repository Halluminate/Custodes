# Changes: SpreadsheetBench 2 debugging-09_03

Fix summary (from the fix record):

The circular revolver/interest block converges to different values in LibreOffice depending on its starting state, so value grading could never pass, even for the answer key. The check now compares formulas, and the answer key passes it locally. The key's unprompted relabelling of the interest rows is reverted, and one prompt sentence states that a missing row is inserted below the rows it is built from, as the key does for Adj. EBITDA and Total Interest Expense. (cleanup: formula-mode switch replaced by a carve-out of the 289 non-settling circular cells.)

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_09_golden.xlsx

## Fixed

- [F8](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells is a trivial fail because gt_09_golden.xlsx has unconverged iterative cached values that fail under LibreOffice recalculation
  - Change: verifications[0].parameters.answer_position (mode stays 'values'): left out the 289 LBO cells of the circular revolver/interest loop that do not settle under one LibreOffice recalc (rows 67-205 G:N block and LBO!D213/L213; found by scoring the key itself, the key with Excel caches and the key with no caches against the key). graderGuidance range list updated to match. Real scorer: key vs itself PASS 1.0/1.0 (was mod 0.9687), key without caches PASS, previous key cache PASS (only the B175/B178 label fixes differ, within the regression allowance), untouched input FAIL (mod 0.0).
- [F2](../findings.json) (Verification): The GT relabels the interest rows with exact strings an agent cannot infer, and the label cells are graded
  - Change: gt_09_golden.xlsx LBO!B175 'Total Interest' -> 'Cash Interest' and B178 'Cash Interest' -> 'Interest Income' (the input's accurate labels), so both are regression cells again. No other cell, value or style changed.
- [F3](../findings.json) (Verification): Undisclosed structural row insertions and label renames on LBO and Financials sheets required for exact coordinate alignment
  - Change: prompt.md: added after the error list 'If a fix needs a row that is missing from the model, insert a new row directly below the rows it is built from instead of reusing an existing empty row.' This matches the GT's Financials row 18 (Adj. EBITDA below rows 15-17) and LBO row 179 (Total Interest Expense below 175-178). Label renames handled by the GT patch above.
- [F4](../findings.json) (Reward): The grader only accepts a fix that inserts a new row at the exact position the GT uses; any other valid repair fails every shifted cell
  - Change: Same prompt sentence: the GT's row-insertion layout is now stated rather than hidden.
- [F1](../findings.json) (Task Spec): Grader requires an undocumented rearrangement of valid worksheet sections
  - Change: Same prompt sentence.
- [F7](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: Same answer_position carve-out of the non-settling circular loop cells as verifier-correctness-0; the key now passes its own check.
- [F5](../findings.json) (Reward): Golden workbook gt_09_golden.xlsx contains unconverged circular-reference cached values and fails its own verifier upon recalculation
  - Change: Same answer_position carve-out of the non-settling circular loop cells as verifier-correctness-0; the key now passes its own check.
- [F6](../findings.json) (Reward): The ground-truth workbook fails its own verifier after LibreOffice recalculation, so no submission can pass
  - Change: Same answer_position carve-out of the non-settling circular loop cells as verifier-correctness-0; the key now passes its own check.
