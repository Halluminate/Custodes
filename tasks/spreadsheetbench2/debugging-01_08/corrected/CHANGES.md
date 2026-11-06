# Changes: SpreadsheetBench 2 debugging-01_08

Fix summary (from the fix record):

The golden and reference workbooks had stale cached values from LibreOffice data-table evaluation (e.g. LBO!C32 109.5182 instead of 101.3452), so the golden failed its own check. Both were recalculated the same way the verifier treats outputs (data tables frozen, forced LibreOffice recalc), and the golden now scores 1.0.

Changed files (in this folder):

- reference/gt_01_golden.xlsx
- reference/untouched_input_Incorrect Sign Conventions_input.xlsx

## Fixed

- [F4](../findings.json) (Verification): Golden gate: the ground-truth deliverable does not score full reward
  - Change: gt_01_golden.xlsx and untouched_input_Incorrect Sign Conventions_input.xlsx replaced with copies produced by the verifier's own managed_recalculated_xlsx(force_recalculation=True). The golden now scores regression 1.0 / modification 1.0 (was 0.9954 / 0.9672, 65 errors). No formula was changed except that the TABLE() grids in 'Ex 1 - LBO'!AG18:AK49 are stored as their frozen values, as the verifier does for outputs.
- [F5](../findings.json) (Reward): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check cannot pass any formula-preserving submission due to asymmetric data-table recalculation against corrupted ground truth
  - Change: Same recalculated GT and reference files. LBO!C11 = 14.2034, C32 = 101.3452, C37 = 11396.80 now match a recalculated output.
- [F1](../findings.json) (Verification): Ground truth workbook contains corrupted LibreOffice data-table evaluation caches and fails its own verifier
  - Change: Same recalculated GT and reference files (fixes the internally inconsistent caches).
- [F3](../findings.json) (Verification): The answer key fails its own verifier because its cached values are stale
  - Change: Same recalculated GT and reference files. The unedited input still fails (modification 0.0), so the task is not made easier.

## Confirmed findings not fixed

- [F2](../findings.json): Stale ground-truth values cause the golden workbook to fail its own grading
  - Reason: duplicate-of:F3
