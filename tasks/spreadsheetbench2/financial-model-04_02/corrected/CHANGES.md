# Changes: SpreadsheetBench 2 financial-model-04_02

Fix summary (from the fix record):

The prompt now states the single Valuation-sheet bridge the answer key uses for Implied EV/EBITDA.

Changed files (in this folder):

- prompt.md

## Fixed

- [F3](../findings.json) (Verification): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check gives false-negative 0.0 score across all 3 units due to Ratio_Analysis!K41:O41 Implied EV/EBITDA formula mismatch in golden workbook
  - Change: prompt.md: added "For Implied EV/EBITDA, build one implied enterprise value from the Valuation sheet (Target Price times No. of shares outstanding, plus Adjustment for Debt and Minority Interest, less Cash and Marketable Securities and Investments and Others) and divide it by each forecast year's EBITDA." (reproduces golden K41 = 16.636 exactly)
- [F1](../findings.json) (Task Spec): Undisclosed and inconsistent Implied EV/EBITDA convention in Ratio_Analysis!K41:O41 causes valid period-specific solutions to score 0.0
  - Change: prompt.md: added "For Implied EV/EBITDA, build one implied enterprise value from the Valuation sheet (Target Price times No. of shares outstanding, plus Adjustment for Debt and Minority Interest, less Cash and Marketable Securities and Investments and Others) and divide it by each forecast year's EBITDA." (reproduces golden K41 = 16.636 exactly)
- [F2](../findings.json) (Task Spec): The Implied EV/EBITDA answer key uses one undisclosed bridge, so a reasonable alternative build fails the whole task
  - Change: prompt.md: added "For Implied EV/EBITDA, build one implied enterprise value from the Valuation sheet (Target Price times No. of shares outstanding, plus Adjustment for Debt and Minority Interest, less Cash and Marketable Securities and Investments and Others) and divide it by each forecast year's EBITDA." (reproduces golden K41 = 16.636 exactly)
