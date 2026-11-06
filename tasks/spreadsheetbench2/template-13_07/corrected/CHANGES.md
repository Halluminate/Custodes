# Changes: SpreadsheetBench 2 template-13_07

Fix summary (from the fix record):

The answer key deleted the supplied tax-rate note in Normalization!B33 and graded the blank 2025E assumption cells I23:I26 as must-stay-blank. B33 is restored in the golden, and I23:I26 are dropped from answer_position so filling or leaving them both pass. Full pass: no further change.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_13_07_golden.xlsx

## Fixed

- [F1](../findings.json) (Verification): The answer key deletes an input note (B33) without being asked, so a correct solution that keeps it scores 0
  - Change: gt_13_07_golden.xlsx Normalization!B33 restored to the input text '• Statutory tax rate for adjustment tax effects: 25%' with the input cell's formatting; it is now an unchanged (regression) cell. Golden scores 1.0 locally; the old golden (B33 deleted) now fails.
- [F3](../findings.json) (Verification): Grader requires deleting a supplied tax-rate assumption
  - Change: Same B33 restore in gt_13_07_golden.xlsx.
- [F2](../findings.json) (Verification): The answer key leaves the 2025E assumption cells (I23:I26) blank even though it projects 2025E, so filling them fails
  - Change: verifications[0].parameters.answer_position 'Normalization'!B2:I35 -> 'Normalization'!B2:I22,'Normalization'!B23:H26,'Normalization'!B27:I35 (I23:I26 not compared). Golden with I23:I26 filled with the averages scores 1.0 locally, as does the golden with them blank.
- [F4](../findings.json) (Verification): Golden workbook penalizes completing the 2025E assumptions
  - Change: Same answer_position change; grader guidance range text updated to match.
