# Changes: SpreadsheetBench 2 template-03_01

Fix summary (from the fix record):

The answer key left the Acquirer and Target total assets blank, and the prompt's 'fill all blank cells' did not say which cells stay blank. The 35% tax rate in C9 also had no label. C14/D14 are now filled in the answer key, the prompt gets one sentence on which lines are filled only in the Consolidated column, and B9 is labelled 'Tax rate' in the input and both reference workbooks.

Changed files (in this folder):

- prompt.md
- reference/gt_03_01_golden.xlsx
- reference/untouched_input_03_01_input.xlsx
- inputs/03_01_input.xlsx

## Fixed

- [F1](../findings.json) (Task Spec): Undisclosed cell-filling scope and unlabelled tax rate assumption (C9) cause valid consolidation tables to fail both regression and modification checks
  - Change: gt_03_01_golden.xlsx M&A_Consolidation!C14 =SUM(C12:C13) (3400) and D14 =SUM(D12:D13) (330) added. One sentence appended to the prompt's Instruction line: 'For Net income to common, Dividends and the cash flow statement, fill only the Consolidated column and leave the other columns of those lines blank.' (The remaining blank Balance and NCI cells are zero, and the verifier already treats a blank as equal to 0.) B9 = 'Tax rate' (B8's style) added to 03_01_input.xlsx, untouched_input_03_01_input.xlsx and gt_03_01_golden.xlsx. The patched GT scores reg 1.0 / mod 1.0 locally.
- [F4](../findings.json) (Verification): The instruction says to fill ALL blank cells, but the answer key leaves many cells blank and the grader rejects any extra values
  - Change: Same as above: GT C14/D14 filled, and the prompt sentence names the lines that are filled only in the Consolidated column (rows 30, 31 and 35-40).
- [F5](../findings.json) (Task Spec): The tax rate the answer key needs has no label; the only candidate (C9 = 35%) also equals the NCI share
  - Change: B9 label 'Tax rate' added next to C9 = 0.35 in the agent input (03_01_input.xlsx), the reference input (untouched_input_03_01_input.xlsx) and the GT. No other cell changed.
- [F3](../findings.json) (Verification): Completing blank total-assets cells is penalized by the verifier
  - Change: GT M&A_Consolidation!C14 =SUM(C12:C13) = 3400 and D14 =SUM(D12:D13) = 330, so filled total assets now match.
- [F2](../findings.json) (Environment & Infra): The tax-rate assumption has no label
  - Change: B9 = 'Tax rate' added in the input, the untouched reference input and the GT.
