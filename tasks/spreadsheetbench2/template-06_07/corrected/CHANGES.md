# Changes: SpreadsheetBench 2 template-06_07

Fix summary (from the fix record):

The day-count convention for the monthly balance forecast (single-month flow x days / 365), the unlabeled prepaid-days row 31 with whole-number rounding, and averaged quarterly/FY balances were nowhere stated and cannot be inferred from the Q1 actuals, which fit no convention. One prompt sentence now states the answer key's convention; the answer key is unchanged.

Changed files (in this folder):

- prompt.md

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: Verifier scores 0.0 across all runs due to all-or-nothing modification pass criteria against inconsistent ground truth
  - Change: prompt.md: added one sentence after 'Ensure that all formulas, references, and calculations are correct.' stating the GT convention (month flow x days / 365, prepaids from row 31 rounded to whole numbers, quarterly and FY balances averaged).
- [F2](../findings.json) (Verification): Ground truth uses unannualized 365-day denominator on monthly Revenue/COGS and unlabeled row 31 for Prepaid Expenses, contradicting Q1 historical actuals
  - Change: Same prompt sentence; it also names row 31 as the prepaid days and the whole-number rounding of prepaids.
- [F1](../findings.json) (Verification): Answer key divides monthly revenue/COGS by 365, so forecast balances fall 4-10x below the actuals
  - Change: Same prompt sentence: the /365 on single-month flows is now the stated convention, so a model following the prompt matches the key (the GT itself scores 1.0/1.0 after LibreOffice recalc locally).
- [F3](../findings.json) (Verification): Answer key applies an annual denominator to monthly operating flows
  - Change: Same prompt sentence.
