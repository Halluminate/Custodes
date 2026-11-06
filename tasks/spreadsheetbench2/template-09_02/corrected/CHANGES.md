# Changes: SpreadsheetBench 2 template-09_02

Fix summary (from the fix record):

The one-line instruction left the key's conventions unstated (Year 1 = Entry EBITDA, beginning-balance interest, full cash sweep, and mixed signs: outflows and repayments negative, schedule interest positive). Two prompt sentences now state them; the key and grading are unchanged.

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, major, not in findings.json: Undisclosed cash-flow and debt-schedule sign convention
  - Change: problemStatement: added one sentence to the Instruction: "Show interest, tax, capital expenditure and repayments as negative values in the cash flow and repayment rows, and show interest expense within each debt schedule as a positive value." (the key's convention: C10:C15 negative, e.g. C10 =-C23, C13 =-SharedData!C9*SUM(C9:C12), C15 =-SharedData!C8*C9; C21 =-MIN(C20,C16); C23 =SharedData!C15*C20 positive).
- other finding, major, not in findings.json: Debt and cash-flow sign convention is never stated, but the all-or-nothing grader requires the ground truth's mixed signs
  - Change: problemStatement: added one sentence to the Instruction: "Show interest, tax, capital expenditure and repayments as negative values in the cash flow and repayment rows, and show interest expense within each debt schedule as a positive value." (the key's convention: C10:C15 negative, e.g. C10 =-C23, C13 =-SharedData!C9*SUM(C9:C12), C15 =-SharedData!C8*C9; C21 =-MIN(C20,C16); C23 =SharedData!C15*C20 positive).
- other finding, major, not in findings.json: Ambiguous modeling conventions for Year 1 Entry EBITDA, interest calculation basis, and tax base
  - Change: problemStatement: added one sentence to the Instruction: "Year 1 EBITDA equals Entry EBITDA, interest is charged on each tranche's beginning balance, and all cash available is swept to repay debt." (the key's C9 =SharedData!C6, C23 =SharedData!C15*C20, C21 =-MIN(C20,C16)). No grading change.
- other finding, major, not in findings.json: Unclear whether 'Entry EBITDA' is the Year 1 value or the base the Year 1 growth applies to; the answer key takes the first reading and every downstream cell depends on it
  - Change: problemStatement: added one sentence to the Instruction: "Year 1 EBITDA equals Entry EBITDA, interest is charged on each tranche's beginning balance, and all cash available is swept to repay debt." (the key's C9 =SharedData!C6, C23 =SharedData!C15*C20, C21 =-MIN(C20,C16)). No grading change.
- other finding, major, not in findings.json: The modelling conventions behind the expected answer are never specified (100% cash sweep, interest on beginning balance, leverage on ending debt)
  - Change: problemStatement: added one sentence to the Instruction: "Year 1 EBITDA equals Entry EBITDA, interest is charged on each tranche's beginning balance, and all cash available is swept to repay debt." (the key's C9 =SharedData!C6, C23 =SharedData!C15*C20, C21 =-MIN(C20,C16)). No grading change.
