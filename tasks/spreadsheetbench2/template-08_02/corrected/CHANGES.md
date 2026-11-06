# Changes: SpreadsheetBench 2 template-08_02

Fix summary (from the fix record):

No task change. The only true finding is the sandbox missing openpyxl/pandas/numpy with pip blocked by the proxy. That is environment infrastructure, and the image needs fixing. Full pass: prompt now states the average-balance interest basis and the negative sign for interest expense.

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, major, not in findings.json: Undisclosed sign convention for interest expense lines in Debt Schedule and Summary sections
  - Change: Prompt: added one sentence after the instruction: Calculate interest on the average of each period's beginning and ending balances, and show interest expense as a negative number. (key: C25 -52.5 = -3500*6%/4, D25 -67.5 = -avg(3500,5500)*6%/4, C18 -37.5, C35 3.75 = avg(1200,0)*2.5%/4; rows 40/42 negative). Answer key unchanged.
- other finding, major, not in findings.json: Unstated interest conventions (average vs beginning balance; sign of expense rows) decide pass/fail on an all-or-nothing grade
  - Change: Same prompt sentence (states the average-balance basis and the sign).
