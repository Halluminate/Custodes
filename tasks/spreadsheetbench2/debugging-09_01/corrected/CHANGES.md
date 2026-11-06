# Changes: SpreadsheetBench 2 debugging-09_01

Fix summary (from the fix record):

gt_09_golden.xlsx was saved with an unconverged circular revolver/interest loop, so its cached values (for example LBO!K138 698.75 vs formula 606.18, D213 '6% / 1.4x') failed its own recalculating verifier. Cached values of the 257 affected formula cells were replaced with the converged fixed point from repeated LibreOffice recalculation; formulas, styles and every other cell are unchanged. The 388 circular LBO cells that do not settle in one LibreOffice recalculation (from an openpyxl-saved output or from the input's unconverged caches) are also left out of answer_position and the guidance range text, so the result no longer depends on how the output was saved. Real SB2 scorer: golden 1.0, golden re-saved with openpyxl 1.0, input + key formulas saved with openpyxl 1.0, untouched input fails (mod 0.05; the G66:N66 and Financials row 18 fixes stay graded).

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_09_golden.xlsx

## Fixed

- [F4](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: gt_09_golden.xlsx: cached values of 257 formula cells on LBO (circular revolver block and its downstream rows, incl. 132-138, 175-201, D213/L213) set to the converged values (recalculated until stable). Golden now scores 1.0 locally (regression 1.0, modification 1.0). The 388 circular LBO cells that do not settle in one LibreOffice recalculation (from an openpyxl-saved output or from the input's unconverged caches) are also left out of answer_position and the guidance range text, so the result no longer depends on how the output was saved. Real SB2 scorer: golden 1.0, golden re-saved with openpyxl 1.0, input + key formulas saved with openpyxl 1.0, untouched input fails (mod 0.05; the G66:N66 and Financials row 18 fixes stay graded).
- [F5](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells is a trivial fail because recalculating the golden workbook in LibreOffice diverges from its unconverged cached values
  - Change: Same golden cache fix; the verifier compares against converged values that a single forced recalculation of the golden reproduces. The 388 circular LBO cells that do not settle in one LibreOffice recalculation (from an openpyxl-saved output or from the input's unconverged caches) are also left out of answer_position and the guidance range text, so the result no longer depends on how the output was saved. Real SB2 scorer: golden 1.0, golden re-saved with openpyxl 1.0, input + key formulas saved with openpyxl 1.0, untouched input fails (mod 0.05; the G66:N66 and Financials row 18 fixes stay graded).
- [F3](../findings.json) (Reward): Ground-truth workbook has unconverged circular-reference cached values and fails its own value-mode verifier
  - Change: Same golden cache fix (e.g. H124 now equals H133, K138 = 1800 - K135).
- [F2](../findings.json) (Reward): The ground-truth workbook's cached values are internally inconsistent (the circular revolver/interest roll-forward does not tie), so the golden fails its own verifier after LibreOffice recalculation and the task cannot be passed
  - Change: Same golden cache fix: opening revolver balances now equal prior closing balances; D213/L213 read '6% / 1.3x'.
- [F1](../findings.json) (Reward): Ground-truth workbook contains inconsistent cached values and fails its own verifier
  - Change: Same golden cache fix (L103 = L135, G124 = G133).
