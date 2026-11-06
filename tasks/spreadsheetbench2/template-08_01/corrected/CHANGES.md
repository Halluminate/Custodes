# Changes: SpreadsheetBench 2 template-08_01

Fix summary (from the fix record):

The answer key added the negative term loan interest cell into the revolver formula, so interest paid lowered the revolver. The revolver formula now subtracts the negative interest cell (C7 = 1771.96), and one prompt sentence says TL_Interest is the positive amount paid.

Changed files (in this folder):

- prompt.md
- reference/gt_08_01_golden.xlsx

## Fixed

- [F3](../findings.json) (Task Spec): Internal contradiction in modeling notes and golden solution regarding the sign convention of interest expense and its use in the closed-form Revolver Balance formula
  - Change: gt_08_01_golden.xlsx: DebtSchedule!C7:G7 changed from ...-C20-C15+C12... to ...-C20-C15-C12... (C7 1370.94 -> 1771.96, G7 -1404.03 -> 594.83). Rows 11 and 13 recalculated in LibreOffice, so all interest expenses are now negative. No other cell changed.
- [F2](../findings.json) (Verification): The answer key adds term loan interest with the wrong sign in the revolver formula, so it counts interest paid as cash coming in
  - Change: Same GT edit to DebtSchedule!C7:G7.
- [F1](../findings.json) (Task Spec): The sign convention for interest and revolver lines is not stated, and the grader is all-or-nothing
  - Change: Prompt: added one sentence after the instruction saying TL_Interest in the revolver formula is the term loan interest paid as a positive amount, while the interest expense rows stay negative per the FN note.

## Confirmed findings not fixed

- [F4](../findings.json): Prescribed revolver formula does not reconcile the cash flows
  - Reason: cannot-fix-safely: reconciling cash to 980 would mean adding term loan issuance and repayment to the prescribed closed-form formula in DebtSchedule!B41 of the input workbook. That rewrites the benchmark's stated method rather than removing a key error.
