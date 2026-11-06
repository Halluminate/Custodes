# Changes: SpreadsheetBench 2 template-09_04

Fix summary (from the fix record):

The unstated negative sign for debt repayments, which failed all three runs, is now stated in the prompt.

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, major, not in findings.json: Unstated negative-sign convention for debt repayments is required by the all-or-nothing values check
  - Change: Prompt: added 'Show debt repayments as negative values.' after the instruction (key: C19:M19 =-MIN(C23,C16), C20:M20 =-MIN(C28,C16+C19), rows 24/29 link them and Ending = Beginning + Repayment). All 3 runs had the right magnitudes and balances but positive repayments, failing 22 cells. Answer key unchanged.
- other finding, major, not in findings.json: Undisclosed negative sign convention for debt repayment rows (rows 19, 20, 24, 29) and unverified zero-valued subordinated debt repayment cells
  - Change: Same prompt sentence as another finding (not listed). The blank-vs-0 subordinated repayment point needs no change: the correct value is 0, so blank and 0 are value-identical.
