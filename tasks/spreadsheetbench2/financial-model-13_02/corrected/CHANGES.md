# Changes: SpreadsheetBench 2 financial-model-13_02

Fix summary (from the fix record):

The cell check no longer grades the FY25A Revenue Summary cells (Revenue Drivers H8:H13), which the prompt does not request, so a literal FY26-FY30 solution can pass.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check gives false-negative 0.0 scores on all 3 units due to uninstructed FY25A cells in ground truth
  - Change: verifications[0].answer_position: 'Revenue Drivers'!B2:M44 split into 'Revenue Drivers'!B2:M7,'Revenue Drivers'!B8:G13,'Revenue Drivers'!I8:M13,'Revenue Drivers'!B14:M44, dropping the FY25A Revenue Summary cells H8:H13 that the prompt (FY26-FY30) never asks for; no other sheet references them. graderGuidance range text updated to match. Checked locally with the verifier code: the golden with H8:H12 left blank (a literal FY26-FY30 solution) went from mod 0.9952 (H8/H10/H13 errors) to reg 1.0 / mod 1.0; the golden still scores 1.0 and the untouched input still fails.
- [F2](../findings.json) (Task Spec): Task instructions ask for Revenue Summary for FY26–FY30 only, but ground truth and verifier require FY25A (column H) to be populated as well
  - Change: Same answer_position change (Revenue Drivers H8:H13 excluded).
- [F3](../findings.json) (Verification): Verifier grades FY25A Revenue Summary cells, but the instruction only asks for FY26–FY30
  - Change: Same answer_position change (Revenue Drivers H8:H13 excluded).
- [F1](../findings.json) (Task Spec): Verifier requires FY25 revenue calculations outside the requested forecast period
  - Change: Same answer_position change (Revenue Drivers H8:H13 excluded).
