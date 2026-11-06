# Changes: SpreadsheetBench 2 financial-model-10_02

Fix summary (from the fix record):

Valuation!H60:L64 is an Excel data table whose golden values move with the WACC the agent fills in, but the grader freezes data-table caches instead of recalculating them, so correct work saved with openpyxl fails all 25 cells. That grid is removed from answer_position, and WACC (E67) is still graded directly.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F1](../findings.json) (Reward): The grader fails correct work saved with openpyxl, the tool the prompt recommends, because 25 Valuation data-table cells come back empty
  - Change: Verifier parameter answer_position: "'Valuation'!C3:O95" split into C3:O59, C60:G64, M60:O64 and C65:O95, dropping only the 25 TABLE() cells H60:L64 (the only data-table cells in the workbook). Same range change in grader_guidance.md. Ids, names, function, weight and mode unchanged.
- other finding, major, not in findings.json: The answer key's forecast 'average price per share' uses only FY13 and breaks the model's own averaging convention, so a reasonable alternative fails
  - Change: Prompt, one sentence changed: "In the Assumptions sheet, calculate average price per share under Share Repurchases, then ..." -> "In the Assumptions sheet, calculate average price per share under Share Repurchases for 2014F–2018F by holding the FY2013 average price per share flat, then ...". The key (K118 =IFERROR(J119/J117,""), L118:O118 = prior column) is the original model formula, the same pre-filled K118:O118 in the 10_01/03/04/05 siblings; the prompt now states it.
- other finding, major, not in findings.json: Undisclosed forecast convention for Average Price Per Share under Share Repurchases (Assumptions!K118:O118) vs. 2-year historical average used throughout the sheet
  - Change: Same prompt sentence change as another finding (not listed).
