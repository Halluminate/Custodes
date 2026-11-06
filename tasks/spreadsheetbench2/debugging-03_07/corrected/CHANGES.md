# Changes: SpreadsheetBench 2 debugging-03_07

Fix summary (from the fix record):

Full pass: answer key extended with the QA-named audit fixes (H31 typo, J31:N31 header suffix, J67:N67 sign, Valuation Bridge C7 units); LBO I16 excluded from answer_position.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_03_golden.xlsx

## Fixed

- other finding, major, not in findings.json: The prompt asks for a full audit, but the grader only checks three INDEX/MATCH fixes and fails the whole workbook if more than 8 other cells change
  - Change: gt_03_golden.xlsx corrected at XML level for the QA-named errors with one defensible fix: LBO H31 '(S in millions)' -> '($ in millions)'; J31:N31 suffix 'E' -> 'P' to match the forecast headers J10:N10 and R10:V10 (cached 2018P..2022P); J67:N67 =+J58+J62 -> =+J58-J62 to match J63 (values stay 0); Valuation Bridge C7 =(LBO!V12-LBO!C25) -> =(LBO!V12-LBO!C25)*LBO!N13 (value stays 0). LBO I16 (blank 2017 D&A; the projected income statement has no 2017 D&A to link) has no single defensible fix and is left out of answer_position. The 'keep minimum cash in the sweep' idea names no specific cells and is not encoded. answer_position 'LBO'!B1:V70 -> 'LBO'!B1:V15,'LBO'!B16:H16,'LBO'!J16:V16,'LBO'!B17:V70.
- other finding, minor, not in findings.json: The golden file's Valuation Bridge adds a multiple to dollar amounts
  - Change: GT Valuation Bridge C7 now =(LBO!V12-LBO!C25)*LBO!N13 (dollars); cached 0 unchanged.
