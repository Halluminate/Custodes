# Changes: SpreadsheetBench 2 template-06_25

Fix summary (from the fix record):

Uncued FY ex-gas growth cell RevenueDrivers!H14 left out of answer_position.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check returns false negative (score 0.0) across all 3 units due to unformatted cell RevenueDrivers!H14
  - Change: answer_position 'RevenueDrivers'!B2:H50 -> 'RevenueDrivers'!B2:H13,'RevenueDrivers'!B14:G14,'RevenueDrivers'!B15:H50 (H14 left out); guidance range and note updated. Real scorer: golden 1.0, golden with H14 blank 1.0, untouched input 0.0.
- other finding, major, not in findings.json: Undisclosed requirement to populate unformatted assumption cell RevenueDrivers!H14 causes binary 0.0 score
  - Change: Same answer_position edit (H14 left out).
- other finding, major, not in findings.json: The answer key expects FY totals in row 14, but the FY cells of its inputs (rows 12 and 13) are blank, and pass/fail is all-or-nothing
  - Change: Same answer_position edit (H14 left out).
