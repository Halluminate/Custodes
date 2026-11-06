# Changes: SpreadsheetBench 2 financial-model-10_04

Fix summary (from the fix record):

Valuation!H60:L64 are Excel data-table (TABLE) cells that the verifier's LibreOffice pass cannot recompute, so any workbook saved with openpyxl (the recommended tool) reads them as empty and fails. Those 25 cells are dropped from answer_position; their inputs stay graded. Full pass: prompt now names the COGS driver (Growth YoY) and the Implied EV/EBITDA construction the key uses.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F1](../findings.json) (Reward): Any solution saved with openpyxl, the tool the prompt recommends, scores 0 because its 25 sensitivity-table cells come back empty
  - Change: verifications[0].parameters.answer_position: 'Valuation'!C3:O95 -> 'Valuation'!C3:O59,'Valuation'!C60:G64,'Valuation'!M60:O64,'Valuation'!C65:O95 (skips the 25 TABLE cells H60:L64). Locally the golden re-saved by openpyxl now scores 1.0 (was 0.0), the golden still scores 1.0 and the untouched input still scores 0.0. Grader guidance range text updated.
- other finding, major, not in findings.json: Undisclosed driver choice for Total COGS in Assumptions (Growth YoY vs. As a % of revenue)
  - Change: Prompt: added one sentence after the Assumptions instruction: Forecast Total COGS by growing the prior year at the Growth YoY rates in row 15. (key: Assumptions!K14 =J14*(1+K15) ... O14). Answer key unchanged.
- other finding, major, not in findings.json: Undisclosed formula convention for Implied EV/EBITDA in Ratio_Analysis (Valuation sheet static EV vs. Ratio_Analysis period EV)
  - Change: Prompt: added one sentence after the Ratio Analysis instruction: For Implied EV/EBITDA, build one implied enterprise value from the Valuation sheet (Target Price times No. of shares outstanding, plus Adjustment for Debt and Minority Interest, less Cash and Marketable Securities and Investments and Others) and divide it by each forecast year's EBITDA. (reproduces key K41:O41; same wording as the other McDonalds-model copy). Answer key unchanged.
