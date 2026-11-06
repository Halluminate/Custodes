# Changes: SpreadsheetBench 2 template-14_03

Fix summary (from the fix record):

Took the sign-ambiguous Sales Expenses cell C48 out of answer_position. Net Sale Proceeds is still graded.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: SpreadsheetBench 2 official cell check: Verifier fails all 3 attempts (score 0.0) over an unstated sign convention on NOI_Projection!C48 despite identical Net Sale Proceeds
  - Change: answer_position now leaves out C48 only ('NOI_Projection'!B2:G47,B48,D48:G48,B49:G49), so either sign passes while Net Sale Proceeds C49 is still compared. Real scorer: golden 1.0/1.0, positive-C48 variant 1.0/1.0 (was mod 0.9818), untouched input mod 0.0 (fails).
- other finding, major, not in findings.json: Undisclosed and internally inconsistent sign convention for Sales Expenses (NOI_Projection!C48)
  - Change: answer_position now leaves out C48 only ('NOI_Projection'!B2:G47,B48,D48:G48,B49:G49), so either sign passes while Net Sale Proceeds C49 is still compared. Real scorer: golden 1.0/1.0, positive-C48 variant 1.0/1.0 (was mod 0.9818), untouched input mod 0.0 (fails).
- other finding, major, not in findings.json: Sign convention for Sales Expenses (and vacancy rows) is unstated, and the all-or-nothing grader fails a positive-sign answer
  - Change: answer_position now leaves out C48 only ('NOI_Projection'!B2:G47,B48,D48:G48,B49:G49), so either sign passes while Net Sale Proceeds C49 is still compared. Real scorer: golden 1.0/1.0, positive-C48 variant 1.0/1.0 (was mod 0.9818), untouched input mod 0.0 (fails).
