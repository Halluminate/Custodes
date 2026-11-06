# Changes: SpreadsheetBench 2 debugging-07_08

Fix summary (from the fix record):

The circular LBO debt schedule (LBO & Lenders S49:X59) never settles in a single LibreOffice recalculation, so its values depend on the starting cache and even the golden workbook failed. Those circular cells are dropped from answer_position; every sign fix and all other cells stay graded.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_07_golden.xlsx

## Fixed

- [F6](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells cannot pass even on the ground-truth workbook due to single-pass LibreOffice recalculation of circular references
  - Change: verifications[0].parameters.answer_position: 'LBO & Lenders'!B2:Z65 split into ranges that skip the circular cells X46:X47, S49:X51, S53:X53, S57:X59. Golden, golden re-saved without cache, and input+golden formulas re-saved by openpyxl now all score 1.0 locally; untouched input still scores 0.
- [F5](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: Same answer_position change; gt_07_golden.xlsx now passes its own verifier locally (regression 1.0, modification 1.0).
- [F3](../findings.json) (Reward): Golden workbook gt_07_golden.xlsx has unconverged circular-reference values on LBO & Lenders, causing even the golden file itself to fail verification
  - Change: Same answer_position change removes the unconverged circular LBO cells from the comparison.
- [F2](../findings.json) (Reward): Ground-truth workbook fails its own verifier after the forced LibreOffice recalc (circular LBO debt schedule), so even a perfect answer scores 0
  - Change: Same answer_position change removes the unconverged circular LBO cells from the comparison.
- [F4](../findings.json) (Reward): Golden workbook fails its own forced-recalculation grading
  - Change: Same answer_position change removes the unconverged circular LBO cells from the comparison.
- other finding, major, not in findings.json: Broad audit instruction conflicts with strict 99.8% regression threshold when workbook contains other genuine formula defects
  - Change: files/gt/gt_07_golden.xlsx (built on the critical-pass key, XML edits): 'DCF Model'!D85:F85 ='BS & CF'!E10/F10/G10 -> E9/F9/G9 (Inventory, not PP&E); 'Equity Returns'!I57 '-1' -> '-I56', H82/I82 '-1' -> '-H81'/'-I81' (as D57, C82:D82); H70/I70 -$D$36 -> -$I$36 and H86/I86 -$D$35 -> -$I$35 (Scenario 2 equity, as H69 and H81); H97:H121 IPMT period A97..A121 -> F97..F121 (same values); 'Margin Analysis'!C25:E25 '*1000' removed and C22 5,682,000 -> 5,862,000 (the transposed vitamins revenue; DCF Model D10 5,862 and Margin C11 6,320,000 both imply it), so C25 = C11 = 6,320,000. 39 cells; cached values of their 115 dependents refreshed from the verifier's LibreOffice recalc (circular LBO cell X47, already ungraded, left untouched). Real scorer (values mode, prepared answer_position): new key vs itself PASS; input plus all 50 key changes PASS after forced recalc; untouched input FAIL (mod 0.0); old key FAIL (mod 0.434).
- other finding, major, not in findings.json: Open-ended 'audit and fix thoroughly' instruction, but all-or-nothing grading accepts only the ground truth's specific sign flips
  - Change: Same key change as another finding (not listed).
- other finding, major, not in findings.json: Ground truth leaves an inconsistent formula in Equity Returns I57 that an auditor would fix
  - Change: Same key change as another finding (not listed).
- other finding, major, not in findings.json: Answer key requires using property and equipment as inventory
  - Change: Same key change as another finding (not listed).
- other finding, major, not in findings.json: Equity-return answer key preserves an incorrect preference calculation
  - Change: Same key change as another finding (not listed).
- other finding, major, not in findings.json: Revenue totals retained in the golden do not reconcile with their components
  - Change: Same key change as another finding (not listed).

## Confirmed findings not fixed

- [F1](../findings.json): Task prompt advertises Pandas, openpyxl, and numpy in the Python environment, but system python3 lacks those packages for the model user
  - Reason: infra
