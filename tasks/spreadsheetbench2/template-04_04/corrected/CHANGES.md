# Changes: SpreadsheetBench 2 template-04_04

Fix summary (from the fix record):

The sheet's footnote asks for deductions as negatives while the key stores Tax Expense as positive; the tax row is no longer compared, and NOPAT/FCF still are.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Footnote 'Express deductions as negative values' conflicts with the GT's positive Tax Expense row
  - Change: verifications[0].parameters.answer_position: 'FCF_Calc'!B2:G30 -> 'FCF_Calc'!B2:G22,'FCF_Calc'!B23:C23,'FCF_Calc'!B24:G30 (D23:G23 Tax Expense no longer compared; NOPAT D24:G24 and FCF D28:G28 still are, and they are sign-independent). graderGuidance notes the exclusion. Real SB2 scorer: key 1.0; key with negative tax and NOPAT = EBIT + Tax 1.0 (was 0, mod 0.8889); untouched input 0.0.
