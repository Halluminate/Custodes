# Changes: SpreadsheetBench 2 debugging-01_05

Fix summary (from the fix record):

The answer key and reference input carried stale cached values from an Excel data-table pass, while the grader recalculates the agent's file, so even the key failed (65 regression errors). The 65 cached values are now the recalculated ones in both files. The missing-openpyxl finding is an environment issue and left as infra.

Changed files (in this folder):

- reference/gt_01_golden.xlsx
- reference/untouched_input_Incorrect Average_input.xlsx

## Fixed

- [F2](../findings.json) (Verification): Golden gate: the ground-truth deliverable does not score full reward
  - Change: gt_01_golden.xlsx and the grader's reference copy untouched_input_Incorrect Average_input.xlsx: replaced the 65 stale cached values left by the last data-table pass (e.g. 'Ex 1 - LBO'!C11 18.2034 -> 14.2034, C32 109.5182 -> 101.3452, plus dependants in Ex 1, Ex 2 and Ex 5) with the values the grader's own LibreOffice recalculation (data tables frozen) produces. Only <v> elements were edited, no formulas or formats. Locally, the recalculated key now scores regression 1.0 / modification 1.0 against itself (was 0.9925), and the untouched input still fails.
- [F3](../findings.json) (Verification): SpreadsheetBench 2 official cell check: Verifier recalculates only output_path in LibreOffice while reading stale Excel Data Table cached values from gt_path, causing guaranteed 65-cell regression failure
  - Change: gt_01_golden.xlsx and the grader's reference copy untouched_input_Incorrect Average_input.xlsx: replaced the 65 stale cached values left by the last data-table pass (e.g. 'Ex 1 - LBO'!C11 18.2034 -> 14.2034, C32 109.5182 -> 101.3452, plus dependants in Ex 1, Ex 2 and Ex 5) with the values the grader's own LibreOffice recalculation (data tables frozen) produces. Only <v> elements were edited, no formulas or formats. Locally, the recalculated key now scores regression 1.0 / modification 1.0 against itself (was 0.9925), and the untouched input still fails.
- [F1](../findings.json) (Verification): Stale golden-workbook values cause the correct workbook to fail grading
  - Change: gt_01_golden.xlsx and the grader's reference copy untouched_input_Incorrect Average_input.xlsx: replaced the 65 stale cached values left by the last data-table pass (e.g. 'Ex 1 - LBO'!C11 18.2034 -> 14.2034, C32 109.5182 -> 101.3452, plus dependants in Ex 1, Ex 2 and Ex 5) with the values the grader's own LibreOffice recalculation (data tables frozen) produces. Only <v> elements were edited, no formulas or formats. Locally, the recalculated key now scores regression 1.0 / modification 1.0 against itself (was 0.9925), and the untouched input still fails.
