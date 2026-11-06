# Changes: SpreadsheetBench 2 template-13_02

Fix summary (from the fix record):

Full pass: blank-in-key projected Reported COGS/SG&A and the first growth cell removed from the cell check.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check scores 0.0 on all 3 units despite 1.0000 modification accuracy due to blank cells F8:H8 and F11:H11 being graded as regression errors
  - Change: verifications[0].parameters.answer_position: 'Financial_Normalization'!B2:H31 -> 'Financial_Normalization'!B2:H7,'Financial_Normalization'!B8:E8,'Financial_Normalization'!B9:H10,'Financial_Normalization'!B11:E11,'Financial_Normalization'!B12:H22,'Financial_Normalization'!B23,'Financial_Normalization'!D23:H23,'Financial_Normalization'!B24:H31 (drops projected Reported COGS F8:H8, projected Reported SG&A F11:H11 and 2022 Revenue Growth C23, which the key leaves blank but which an analyst may fairly fill: projected reported = normalized, or NA for the first growth year). All 68 key cells stay graded. graderGuidance updated. Local SB2 scorer: golden 1.0 (old and new), untouched input 0.0, golden with F8:H8=F9:H9, F11:H11=F12:H12 and C23='NA' 0.0 under the old range (reg 0.9507) and 1.0 under the new.
- other finding, major, not in findings.json: Undisclosed constraint and ambiguity on leaving Projected Reported COGS (F8:H8) and Reported SG&A (F11:H11) blank
  - Change: Same answer_position change as verifier-correctness-0.
- other finding, major, not in findings.json: All-or-nothing regression grading fails reasonable fills of projected Reported COGS/SG&A and the 2022 growth cell
  - Change: Same answer_position change as verifier-correctness-0 (covers F8:H8, F11:H11 and C23).
