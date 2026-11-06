# Changes: SpreadsheetBench 2 template-15_02

Fix summary (from the fix record):

Full pass: prompt states the Year-0 NOI convention, and the payoff cell with no single payment count is no longer graded.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Payoff in the answer key assumes 7 amortizing years, but the schedule it checks against shows 8
  - Change: verifications[0].parameters.answer_position (and the range in graderGuidance): 'LoanSizing'!B2:M30 -> 'LoanSizing'!B2:M21,'LoanSizing'!B22:B22,'LoanSizing'!D22:M22,'LoanSizing'!B23:M30, leaving out only C22 'Loan Payoff at Maturity', whose payment count (84 vs 96) has no single reading in the template. Real scorer: golden PASS; golden with the 96-payment payoff 66,812,654.32 FAIL before (mod 0.9773), PASS after; untouched input FAIL (mod 0.0).
- other finding, major, not in findings.json: 'Year 1 NOI' is placed in the Year 0 column, so every NOI and DSCR cell depends on one unstated convention
  - Change: Prompt: one sentence added after the instruction: 'In the Debt Service Schedule, Year 0 uses the Year 1 NOI, and NOI grows at the annual growth rate in each later year.', the convention behind golden C26:M26 (and the DSCR row). Answer key unchanged.
