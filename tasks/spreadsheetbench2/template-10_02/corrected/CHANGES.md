# Changes: SpreadsheetBench 2 template-10_02

Fix summary (from the fix record):

E10, C9 and the sign-ambiguous C31:D32 left out of answer_position.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Ambiguous cell population requirements for E10 and C9 due to inconsistent input template formatting
  - Change: answer_position 'EPS_Accretion'!B2:E42 -> 'EPS_Accretion'!B2:E8,'EPS_Accretion'!B9:B9,'EPS_Accretion'!D9:E9,'EPS_Accretion'!B10:D10,'EPS_Accretion'!B11:E30,'EPS_Accretion'!B31:B32,'EPS_Accretion'!E31:E32,'EPS_Accretion'!B33:E42 (E10, C9 and C31:D32 left out; combined shares still checked in C34:D34, net income in C33:D33); guidance range and note updated. Real scorer: golden 1.0; golden with E10 blank, C9 = acquirer price, C34:D34 computing shares directly and C31:D32 positive with C33 subtracting them 1.0 (0.0 under the old range); untouched input 0.0.
- other finding, major, not in findings.json: Undisclosed sign convention for after-tax interest adjustment rows C31:D32
  - Change: Same answer_position edit (C31:D32 left out).
- other finding, major, not in findings.json: Graded cell E10 (combined diluted shares) gets no cue in the template, and the grade is all-or-nothing
  - Change: Same answer_position edit (E10 left out).
- other finding, major, not in findings.json: No regression tolerance: filling any blank cell in B2:E42 that the golden file leaves empty fails the whole task
  - Change: Same answer_position edit (C9 left out).
