# Changes: SpreadsheetBench 2 financial-model-17_05

Fix summary (from the fix record):

The prompt now says Return on Average Assets uses Profit after Tax, the numerator the key uses; the ungraded combo chart needs a new verifier and is left (cannot-fix-safely).

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, major, not in findings.json: Undisclosed numerator convention for Return on Average Assets (PAT vs. Net Profit after Minority Interest) causes valid solutions to score 0
  - Change: Prompt sentence 'In the Ratio_Analysis sheet, calculate Return on Average Assets for all periods.' -> '... for all periods, using Profit after Tax (PAT).' The key's ROAA (Ratio_Analysis!F19:O19 =Financials!X41/AVERAGE(assets)) uses PAT (Financials row 41), while the neighbouring margin and ROAE rows use Net Profit after Minority Interest (row 47), so both numerators were defensible and the 1% cell check accepts only one. Key and verifier unchanged.
