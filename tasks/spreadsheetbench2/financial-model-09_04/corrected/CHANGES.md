# Changes: SpreadsheetBench 2 financial-model-09_04

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check gives false-negative 0.0 score to units 1 and 2 solely due to unstated Data Table corner cell Valuation!G59
  - Change: verifications[0].parameters.answer_position: 'Valuation'!C3:O96 split into C3:O58, C59:F59, H59:O59, C60:O96, leaving out only the data-table corner cell G59 (=+E48 in the key), which the prompt does not ask for and an explicit-formula grid does not need. graderGuidance range text updated. Real scorer: golden 1.0; golden with G59 blank now PASS (was FAIL, mod 0.9962); untouched input FAIL (mod 0.0).
