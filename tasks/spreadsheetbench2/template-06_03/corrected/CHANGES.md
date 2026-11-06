# Changes: SpreadsheetBench 2 template-06_03

Fix summary (from the fix record):

The growth cells that have no prior period (2023 YoY C46:F46, first QoQ C47) are blank in the key, so writing the usual 'n/a' failed the all-or-nothing check as stray edits. They are now left out of answer_position; every computed cell is still checked.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Vague one-line instruction graded all-or-nothing on every modified cell, with no tolerance for extra cells
  - Change: answer_position 'iPhone_Revenue_Build'!B2:J48 -> "'iPhone_Revenue_Build'!B2:J45,'iPhone_Revenue_Build'!B46:B46,'iPhone_Revenue_Build'!G46:J46,'iPhone_Revenue_Build'!B47:B47,'iPhone_Revenue_Build'!D47:J47,'iPhone_Revenue_Build'!B48:J48" (drops C46:F46 and C47). Real scorer: golden 1.0; input + key formulas 1.0; same with 'n/a' in C46:F46 and C47 1.0 (was 0.0, regression 0.9831); untouched input 0.0 (127 errors). The 'forecast columns only' reading is not accommodated: rows 37-43 and 47-48 are blank for 2023 too and the model is incomplete without them.
