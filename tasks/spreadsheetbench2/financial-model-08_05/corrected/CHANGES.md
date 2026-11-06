# Changes: SpreadsheetBench 2 financial-model-08_05

Fix summary (from the fix record):

The prompt now states how Net Cost of Equity and Debt to Equity are built, and the cell check no longer grades the unrequested Debt to EBITDA and Interest Coverage rows (whose key formulas are also inconsistent).

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F8](../findings.json) (Task Spec): Undisclosed non-standard Net Cost of Equity formula in DCF Valuation!C66 causes all DCF checks to fail
  - Change: prompt.md: the DCF sentence now reads '... calculate Gross Cost of Equity (CAPM on the adjusted risk free rate) and Net Cost of Equity (Gross Cost of Equity divided by one minus the Liquidity Premium, plus the Small Cap Risk Premium).', matching GT C63 =C60+C61*C62 and C66 =C63/(1-C64)+C65.
- [F7](../findings.json) (Task Spec): Net Cost of Equity relies on an unstated, non-standard formula that drives the whole DCF
  - Change: Same prompt DCF sentence change as F8.
- [F4](../findings.json) (Task Spec): Verifier grades unrequested Ratio Analysis rows (Debt to EBITDA and Interest Coverage Ratio) and ambiguous Debt to Equity definition
  - Change: verifications[0].answer_position: 'Ratio Analysis'!B2:H21 -> 'Ratio Analysis'!B2:H19 (rows 20-21 are not requested and nothing else references them); prompt.md Ratio sentence now says Debt to Equity is Long Term Debt divided by Total Shareholders Equity, matching GT C19 ='Balance Sheet'!C18/'Balance Sheet'!C9. graderGuidance range text updated to match.
- [F5](../findings.json) (Verification): Grader requires two Ratio Analysis rows the task never asks for (Debt to EBITDA, Interest Coverage)
  - Change: Same answer_position narrowing to 'Ratio Analysis'!B2:H19 as F4.
- [F3](../findings.json) (Verification): The answer key requires two additional ratios not identified in the task's specific instructions
  - Change: Same answer_position narrowing to 'Ratio Analysis'!B2:H19 as F4.
- [F2](../findings.json) (Verification): Ground-truth Interest Coverage formula is wrong and inconsistent across columns
  - Change: Interest Coverage row 21 is no longer graded after narrowing answer_position to 'Ratio Analysis'!B2:H19, so its inconsistent key formulas no longer affect the score.
- [F6](../findings.json) (Verification): Interest-coverage answer formulas change definition and double-count depreciation
  - Change: Same as F2: row 21 removed from the graded range.

## Confirmed findings not fixed

- [F1](../findings.json): Single-pass recalculation rejects an unchanged golden workbook after an openpyxl save
  - Reason: infra
