# Changes: SpreadsheetBench 2 template-02_06

Fix summary (from the fix record):

No task change. The only true finding is that the sandbox lacks the advertised openpyxl/pandas/numpy and the proxy blocks pip, which is an image/harness defect.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Undisclosed sign convention for 'Less: Minimum operating cash' row in DebtWaterfall
  - Change: answer_position 'DebtWaterfall'!A1:E40 -> 'DebtWaterfall'!A1:E5,'DebtWaterfall'!A6,'DebtWaterfall'!A7:E40 (drops only B6:E6, the sign-ambiguous 'Less: Minimum operating cash' row); the 0.4% calculation is still graded through C5:E5 and row 8. graderGuidance range text updated. Scorer: key 1.0; variant with B6:E6 negative, row 8 =SUM and C5 =-B6 now 1.0 (fails under old range); untouched input fails.
