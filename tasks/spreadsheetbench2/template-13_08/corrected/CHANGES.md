# Changes: SpreadsheetBench 2 template-13_08

Fix summary (from the fix record):

C32 (2018 growth, no prior year) left out of answer_position.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Leaving 2018 sales growth blank is graded as a must-stay-empty cell, so a reasonable 'N/A' or '–' entry fails the whole task
  - Change: answer_position 'FinancialNormalization'!B2:I41 -> 'FinancialNormalization'!B2:I31,'FinancialNormalization'!B32:B32,'FinancialNormalization'!D32:I32,'FinancialNormalization'!B33:I41 (C32 left out); guidance range and note updated. Real scorer: golden 1.0, golden with C32 = 'N/A' 1.0 (0.0 under the old range), untouched input 0.0.
