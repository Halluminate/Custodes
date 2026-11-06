# Changes: SpreadsheetBench 2 template-16_08

Fix summary (from the fix record):

answer_position leaves out the sign-ambiguous Concessions and Vacancy cells (C15:D15, C26:D26); totals are still graded.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Sign convention for contra-revenue deductions vs. operating expenses is not communicated to the agent
  - Change: verifications[0].parameters.answer_position: 'NOI_Analysis'!B2:E52 split so it leaves out only C15:D15 (Concessions) and C26:D26 (Vacancy & Credit Loss), whose sign is not stated; the subtotals D16/D27, EGR, NOI and value are still compared, so the amounts must still be right. graderGuidance range updated to match. Real SB2 scorer: golden 1.0/1.0, positive-deduction variant (D15 =D13*0.03, D16 =D13+D14-D15, D26 =D25*0.06, D27 =D25-D26) 1.0/1.0 (was mod 0.92, fail), untouched input mod 0.0 (fail).
- other finding, major, not in findings.json: All-or-nothing grading depends on an unstated sign convention for the deductions (concessions and vacancy)
  - Change: verifications[0].parameters.answer_position: 'NOI_Analysis'!B2:E52 split so it leaves out only C15:D15 (Concessions) and C26:D26 (Vacancy & Credit Loss), whose sign is not stated; the subtotals D16/D27, EGR, NOI and value are still compared, so the amounts must still be right. graderGuidance range updated to match. Real SB2 scorer: golden 1.0/1.0, positive-deduction variant (D15 =D13*0.03, D16 =D13+D14-D15, D26 =D25*0.06, D27 =D25-D26) 1.0/1.0 (was mod 0.92, fail), untouched input mod 0.0 (fail).
