# Changes: SpreadsheetBench 2 debugging-02_01

Fix summary (from the fix record):

All data-table (TABLE) cells, including the corrupted golden Berk-Hath dividend grid, are removed from the graded range; the four real formula fixes are still graded.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F5](../findings.json) (Verification): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells fails all units due to corrupted ground-truth values in Berk-Hath Investment Package!G10:K14
  - Change: answer_position: left out every =TABLE() data-table cell (DCF!V10:Z14 and 'Berk-Hath Investment Package'!G10:K14, G18:K22, G26:K30; 100 cells, nothing else depends on them). The golden Berk-Hath G10:K14 values are shifted/duplicated rows, and LibreOffice cannot recompute any TABLE grid, so these cells cannot be graded fairly; the rest of the ranges are unchanged.
- [F2](../findings.json) (Verification): Ground truth for Berk-Hath Investment Package sensitivity table (G10:K14) contains corrupted hardcoded values instead of valid Data Table results
  - Change: answer_position: left out every =TABLE() data-table cell (DCF!V10:Z14 and 'Berk-Hath Investment Package'!G10:K14, G18:K22, G26:K30; 100 cells, nothing else depends on them). The golden Berk-Hath G10:K14 values are shifted/duplicated rows, and LibreOffice cannot recompute any TABLE grid, so these cells cannot be graded fairly; the rest of the ranges are unchanged.
- [F1](../findings.json) (Reward): Berk-Hath sensitivity-table cells that must change cannot be produced: the input's TABLE() cache is flattened and LibreOffice cannot recompute it
  - Change: answer_position: left out every =TABLE() data-table cell (DCF!V10:Z14 and 'Berk-Hath Investment Package'!G10:K14, G18:K22, G26:K30; 100 cells, nothing else depends on them). The golden Berk-Hath G10:K14 values are shifted/duplicated rows, and LibreOffice cannot recompute any TABLE grid, so these cells cannot be graded fairly; the rest of the ranges are unchanged.
- [F4](../findings.json) (Verification): Golden dividend sensitivity table contains 20 incorrect values
  - Change: answer_position: left out every =TABLE() data-table cell (DCF!V10:Z14 and 'Berk-Hath Investment Package'!G10:K14, G18:K22, G26:K30; 100 cells, nothing else depends on them). The golden Berk-Hath G10:K14 values are shifted/duplicated rows, and LibreOffice cannot recompute any TABLE grid, so these cells cannot be graded fairly; the rest of the ranges are unchanged.
- [F3](../findings.json) (Reward): Saving with openpyxl, the workflow the prompt recommends, wipes every TABLE() cached value and fails the regression threshold
  - Change: answer_position: left out every =TABLE() data-table cell (DCF!V10:Z14 and 'Berk-Hath Investment Package'!G10:K14, G18:K22, G26:K30; 100 cells, nothing else depends on them). The golden Berk-Hath G10:K14 values are shifted/duplicated rows, and LibreOffice cannot recompute any TABLE grid, so these cells cannot be graded fairly; the rest of the ranges are unchanged. This also removes the regression failures from TABLE caches that openpyxl drops on save.
