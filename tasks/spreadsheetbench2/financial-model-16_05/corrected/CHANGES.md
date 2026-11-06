# Changes: SpreadsheetBench 2 financial-model-16_05

Fix summary (from the fix record):

One prompt clause states the loan-repayment base (opening balance plus new loans). answer_position drops Valuation Summary and Football!G16 (Enterprise Value total row, not a method) and the 48 broken '=assumptions!#ref!' cells L32:S37, which LibreOffice rewrites to '=#REF!' so the golden failed its own check (reg 0.9968). Local SB2 scorer with the new answer_position: golden PASS 1.0/1.0, golden with G16 blank PASS 1.0/1.0, untouched input FAIL (mod 0.0). Before: golden FAIL reg 0.9968.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Ambiguous Loan Repayment basis in BS_Sch!F23:K23 between Opening Balance and Opening Balance plus New Loans
  - Change: prompt.md: the Loan Repayment sentence now reads 'Calculate Loan Repayment for 2022E–2027E by applying the Debt repayment % to the opening balance plus new loans, then calculate Interest Expense ...', which states the golden's convention (BS_Sch F23:K23 =-(F21+F22)*F25). GT unchanged.
- other finding, major, not in findings.json: Base for the debt repayment % is not stated, and the grader accepts only repayment on (opening + new loans)
  - Change: Same prompt sentence (repayment base stated).
- other finding, major, not in findings.json: Golden workbook grades 17 unmentioned blank cells (BS_Sch!G6:K6, Balance Sheet!F11:K11, and Valuation Summary and Football!G16) while the prompt instructs modifying only requested cells
  - Change: answer_position: 'Valuation Summary and Football'!B2:S46 split into B2:S15, B16:F16, H16:S16, B17:S46 so the ambiguous total-row cell G16 (unreferenced elsewhere) is no longer compared. graderGuidance updated with the new ranges. The G6:K6 and F11:K11 parts are inferable and stay graded.
- other finding, minor, not in findings.json: Seed workbook contains permanently broken sensitivity tables
  - Change: answer_position: the 48 broken '=assumptions!#ref!' cells 'Valuation Summary and Football'!L32:S37 are left out (B17:S46 split into B17:S31, B32:K37, B38:S46); their #NAME? dependents L41:S46 compare equal and stay graded. graderGuidance updated with the new ranges. No file changed.
