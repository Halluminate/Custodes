# Changes: FINCH task-144

Fix summary (from the fix record):

NXAVC-1, the before-close day count and the N/A placement are undefined desk conventions. A guidance note accepts any reasonable reading for those rows only.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Undisclosed domain-specific calculation and applicability rules for NYMEX settlement statistics (e.g., NXAVC-1 roll-day substitution and close-date vs. prompt-month windowing)
  - Change: grader guidance: added the task note 'Task note: the workbook does not define NXAVC-1 (row 51), whether the 'day before close' rows (55, 56 and 58) count the close day itself, or which calculable cells should read N/A, so for those rows and for N/A versus a computed value accept any reasonable, consistently applied reading, and judge the remaining filled cells against the reference.' Rows 49, 50, 52-54 and 57 in columns D, G and H stay strictly graded against the reference.
- other finding, major, not in findings.json: The answer key relies on desk conventions that are never stated, and the all-or-nothing rubric fails any other reasonable reading
  - Change: grader guidance: added the task note 'Task note: the workbook does not define NXAVC-1 (row 51), whether the 'day before close' rows (55, 56 and 58) count the close day itself, or which calculable cells should read N/A, so for those rows and for N/A versus a computed value accept any reasonable, consistently applied reading, and judge the remaining filled cells against the reference.' Rows 49, 50, 52-54 and 57 in columns D, G and H stay strictly graded against the reference.
- other finding, major, not in findings.json: Settlement-index definition and N/A applicability rules are missing
  - Change: grader guidance: added the task note 'Task note: the workbook does not define NXAVC-1 (row 51), whether the 'day before close' rows (55, 56 and 58) count the close day itself, or which calculable cells should read N/A, so for those rows and for N/A versus a computed value accept any reasonable, consistently applied reading, and judge the remaining filled cells against the reference.' Rows 49, 50, 52-54 and 57 in columns D, G and H stay strictly graded against the reference.
- other finding, major, not in findings.json: Before-close labels conflict with the reference's inclusive day counting
  - Change: grader guidance: added the task note 'Task note: the workbook does not define NXAVC-1 (row 51), whether the 'day before close' rows (55, 56 and 58) count the close day itself, or which calculable cells should read N/A, so for those rows and for N/A versus a computed value accept any reasonable, consistently applied reading, and judge the remaining filled cells against the reference.' Rows 49, 50, 52-54 and 57 in columns D, G and H stay strictly graded against the reference.
