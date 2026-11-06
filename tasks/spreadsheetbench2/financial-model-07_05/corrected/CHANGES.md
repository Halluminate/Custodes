# Changes: SpreadsheetBench 2 financial-model-07_05

Fix summary (from the fix record):

The golden and reference workbooks were saved by an old LibreOffice that cached #NAME? for the Sales Schedule XLOOKUPs and 0 in 1,177 downstream cells, while the verifier recalculates outputs in a LibreOffice that evaluates XLOOKUP. Both files were recalculated with the verifier's own recalculation, and the golden now scores 1.0.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_07_RealEstate_golden.xlsx
- reference/untouched_input_07_05_RealEstate_input.xlsx

## Fixed

- [F2](../findings.json) (Verification): Golden gate: the ground-truth deliverable does not score full reward
  - Change: gt_07_RealEstate_golden.xlsx and untouched_input_07_05_RealEstate_input.xlsx given the cached values produced by managed_recalculated_xlsx(force_recalculation=True), written at XML level into the original files (formulas, charts and styles unchanged). Golden now scores regression 1.0 / modification 1.0 (was 0.9690, 1,177 errors). The unedited input still fails (modification 0.0).
- [F3](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells trivially fails (scores 0.0) on all valid solutions and on the ground truth itself due to forced LibreOffice recalculation mismatch
  - Change: Same recalculated GT and reference (e.g. Executive Summary!D26 now 274.49 in both, matching a recalculated output).
- other finding, major, not in findings.json: The graded Amount/sf calculation uses construction area instead of saleable area
  - Change: answer_position: 'Construction Schedule (1)'!A1:BJ70 split into A1:BJ9, A10:D10, F10:BJ10 and A11:BJ70 so the ambiguous Amount/sf cell E10 is no longer compared. E10 feeds no other cell. The Mobilization Logistics distribution (O10:T10) stays graded. Real scorer, with the recalculated GT and reference: golden PASS reg 1.0 mod 1.0, unedited input FAIL (mod 0.0).

## Confirmed findings not fixed

- [F1](../findings.json): The golden workbook fails the verifier's forced recalculation
  - Reason: duplicate-of:verifier-correctness-0
