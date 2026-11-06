# Changes: SpreadsheetBench 2 template-14_05

Fix summary (from the fix record):

The sheet's own footnote (B41) says to express deductions as negative numbers, but the answer key kept operating expenses positive while negating only vacancy. The answer key now shows the operating-expense deductions (J35:N39) as negatives, NOI unchanged.

Changed files (in this folder):

- reference/gt_14_05_golden.xlsx

## Fixed

- [F4](../findings.json) (Task Spec): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check fails valid solutions (score 0.0 on all 3 units) due to ambiguous sign convention on J35:N39
  - Change: gt_14_05_golden.xlsx NOI_Projection: J35 =-C28, K35 =-C29, L35 =-C30, M35:M39 =-I*C18, O35:O39 =I+N (was I-N); recalculated so J35:N39 cached values are the negatives of the old ones (e.g. J35 -785000, N35 -2044185.2) and O35:O39 NOI is unchanged. All other cells identical.
- [F3](../findings.json) (Task Spec): Undisclosed and ambiguous sign convention between Vacancy & Credit Loss (H35:H39) and Operating Expenses (J35:N39)
  - Change: Same GT patch: every deduction (vacancy and all operating-expense columns) now follows the B41 footnote.
- [F2](../findings.json) (Verification): The footnote says to show deductions as negative numbers, but the answer key shows operating expenses as positive, and grading is pass/fail
  - Change: Same GT patch; the three runs that negated J35:N39 (regression 1.0, modification 0.6154 failing only on sign) would now match.
- [F1](../findings.json) (Verification): Ground truth contradicts the workbook’s required sign convention
  - Change: Same GT patch.
