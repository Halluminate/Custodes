# Changes: SpreadsheetBench 2 debugging-05_02

Fix summary (from the fix record):

Formula-mode exact matching left as is (critical pass). Full pass: the key now also fixes the named Total Current Assets/Liabilities sums (E59:N59, E67:N67), and the 68 embedded-hardcode formulas the key keeps, which have no single correction, are no longer graded.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_05_golden.xlsx

## Fixed

- other finding, major, not in findings.json: Golden workbook preserves incorrect balance-sheet totals
  - Change: gt_05_golden.xlsx (XML edit of xl/worksheets/sheet1.xml, only these 20 formulas changed): Model!E59:N59 =SUM(X51:X53,X55,X57) -> =SUM(X51,X53,X55,X57) (drops row 52 'Days Unbilled Outstanding' from Total Current Assets) and Model!E67:N67 =SUM(X61:X63,X65) -> =SUM(X61,X63,X65) (drops row 62 'Net Revenue %' from Total Current Liabilities). Cached values refreshed from the verifier's own LibreOffice recalc, 33 cells changed (rows 59, 67, 68 and F69:H69; e.g. E59 245.12 -> 137.738, J59 347.86 -> 238.82). Real scorer (formula mode, new answer_position): new key vs itself reg 1.0 mod 1.0; input plus the 11 planted fixes plus these 20 fixes reg 1.0 mod 1.0; untouched input mod 0.0 (31 errors).
- other finding, major, not in findings.json: Task is named 'Embedded Hardcodes', yet the answer key keeps ~70 embedded-hardcode formulas, and fixing them can fail the run
  - Change: verifications[0].parameters.answer_position (+ graderGuidance range list): the 68 embedded-hardcode formulas the key keeps, which have no single defensible correction (no defined input home for the constants), are left out of the graded ranges so moving them into inputs no longer fails the regression check: 'Financial Overview'!D14:I15, C16:F16, J12, J19 (=142.902/D$12, =C8-179.281, =AVERAGE(360,365), =AVERAGE(77,78)); 'Financial Performance'!E4:E19, H5:H12, L7:M9, L11:M13, L15:M17, L19:M20 (=F4-43.824, =4.503-SUM(L6:L7) ...); 'Transaction Overview'!P7, P17 and Model!U13 (0.25/0.75 weights) and Model!I26 (=AVERAGE(360,365)). Graded cells 9,955 -> 9,887; all other ranges unchanged. Same scorer results as another finding (not listed).

## Confirmed findings not fixed

- [F4](../findings.json): SpreadsheetBench 2 official cell check: Verifier falsely rejects valid weighted-average interest rate formulas at Transaction Overview!L15 and penalizes valid bug fixes as regressions
  - Reason: cannot-fix-safely: formula mode is the benchmark's grading for this embedded-hardcode item. Switching to values mode would turn the hardcode fixes (J45:N45, J91:N91, Transaction Overview!L15) into regression cells, because a hardcode and its formula have the same value, so the task would pass untouched. The verifier has no formula-equivalence option, and no parameter change keeps the check meaningful.
- [F2](../findings.json): Verifier in formula mode enforces exact formula string matching and binary all-or-nothing scoring on multi-way formulas
  - Reason: cannot-fix-safely: formula mode is the benchmark's grading for this embedded-hardcode item. Switching to values mode would turn the hardcode fixes (J45:N45, J91:N91, Transaction Overview!L15) into regression cells, because a hardcode and its formula have the same value, so the task would pass untouched. The verifier has no formula-equivalence option, and no parameter change keeps the check meaningful.
- [F3](../findings.json): Formula-mode grading accepts only the answer key's exact formula text, so correct equivalent fixes score 0
  - Reason: cannot-fix-safely: formula mode is the benchmark's grading for this embedded-hardcode item. Switching to values mode would turn the hardcode fixes (J45:N45, J91:N91, Transaction Overview!L15) into regression cells, because a hardcode and its formula have the same value, so the task would pass untouched. The verifier has no formula-equivalence option, and no parameter change keeps the check meaningful.
- [F1](../findings.json): Task prompt and input styling contradict the ground truth on which cells are errors versus protected inputs
  - Reason: cannot-fix-safely: removing the ambiguity would mean telling the agent that Model!J91:N91 must link to '3-month Term SOFR' December rows, which gives away the injected errors. Adding fixes for the pre-existing E59/E67/I26 quirks to the key would make every agent match those exact formula strings too, which makes the task harder rather than removing the defect.
