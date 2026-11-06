# Changes: SpreadsheetBench 2 template-02_02

Fix summary (from the fix record):

The workbook never stated the sign of repayments or whether interest comes out of the cash sweep, and the key needs negative repayments (they enter the three-point interest average) and no interest deduction. Two prompt sentences now state both conventions, and the input note no longer calls the non-circular beginning-cash link a circular reference.

Changed files (in this folder):

- prompt.md
- inputs/02_02_input.xlsx

## Fixed

- other finding, major, not in findings.json: Undisclosed negative sign convention for debt Repayment rows causes cascade of 21 cell errors in Interest Expense and Total Interest Expense
  - Change: problemStatement: added one sentence to the Instruction: Enter debt repayments as negative values, so each Ending Balance equals the Beginning Balance plus the Repayment. (the key's convention: B13 =-MIN(B9,B12), B14 =B12+B13).
- other finding, major, not in findings.json: Sign convention for repayments is never stated, and the all-or-nothing grader only accepts negative repayments
  - Change: problemStatement: added one sentence to the Instruction: Enter debt repayments as negative values, so each Ending Balance equals the Beginning Balance plus the Repayment. (the key's convention: B13 =-MIN(B9,B12), B14 =B12+B13).
- other finding, major, not in findings.json: Input workbook does not specify whether Cash Available After debt tranches deducts only principal repayment or also interest expense
  - Change: problemStatement: added one sentence to the Instruction: Operating Cash Flow Available is already after interest, so do not deduct interest expense again when computing cash available for debt repayment. (the key's B9 =B4+B7-B8 and B17 =B9+B13 deduct no interest).
- other finding, major, not in findings.json: Cash sweep does not subtract interest, and the input never says so
  - Change: problemStatement: added one sentence to the Instruction: Operating Cash Flow Available is already after interest, so do not deduct interest expense again when computing cash available for debt repayment. (the key's B9 =B4+B7-B8 and B17 =B9+B13 deduct no interest).
- other finding, minor, not in findings.json: Note calls a non-circular link a 'circular reference'
  - Change: files/data/02_02_input.xlsx: DebtWaterfall!A45 note text "This circular reference means..." changed to "This link means..." (one shared string edited at XML level; every other part byte-identical). A45 is outside answer_position, so the key and reference are unchanged. Local check: GT PASS 1.0/1.0, patched untouched input FAIL (mod 0.0).
