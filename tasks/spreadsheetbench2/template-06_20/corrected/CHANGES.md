# Changes: SpreadsheetBench 2 template-06_20

Fix summary (from the fix record):

The prompt's segment-CAGR sentence did not fit this store-driver workbook and the forecast Prior Year Sales per Square Foot rule could not be inferred, so that sentence now states the driver build and the row-20 rule. Period-End C8:G8 and first-year YoY C47/C50, blank in the GT, are taken out of the graded range so following 'Fill in all empty cells' is no longer penalised.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F2](../findings.json) (Task Spec): Contradictory task instruction ('Project each segment using its historical CAGR from Year 1 to Year 3') vs. ground truth and undisclosed formula convention for Row 20 ('Prior Year Sales per Square Foot')
  - Change: prompt.md: replaced 'Project each segment using its historical CAGR from Year 1 to Year 3.' with 'Project FY25E and FY26E from the driver assumptions already in the sheet, setting each forecast year's Prior Year Sales per Square Foot to the prior year's Total Retail Sales divided by that year's ending Total Square Feet.' (matches GT F20=E33/E16, G20=F33/F16).
- [F5](../findings.json) (Task Spec): Instruction/spec/metadata use a mismatched 'segment CAGR' template, but the model has no segments and the answer key uses no CAGR
  - Change: Same prompt sentence replacement: the segment-CAGR template sentence is gone and the driver build is named.
- [F1](../findings.json) (Verification): The answer key uses a driver-based forecast instead of the instructed historical CAGR
  - Change: Same prompt sentence replacement: the instruction no longer asks for a historical CAGR, so it matches the driver-based GT.
- [F4](../findings.json) (Task Spec): Unstated derivation conventions for the forecast and the KPIs; the historical row-20 values don't follow the convention the GT uses for forecast years
  - Change: Same prompt sentence now states the forecast row-20 convention (prior year Total Retail Sales / that year's ending Total Square Feet), the one convention the historicals do not reveal. The other derivations follow the row labels (average sqft = avg of rows 25 and 16, productivity x prior-year sales/sqft) and are left as is.
- [F3](../findings.json) (Verification): Instruction 'Fill in all empty cells' conflicts with ground truth leaving Period-End (C8:G8) and Year 1 YoY % Change (C47, C50) empty
  - Change: Verifier parameter answer_position changed from 'RevenueBuild'!B2:G50 to 'RevenueBuild'!B2:G7,'RevenueBuild'!B8,'RevenueBuild'!B9:G46,'RevenueBuild'!B47,'RevenueBuild'!D47:G47,'RevenueBuild'!B48:G49,'RevenueBuild'!B50,'RevenueBuild'!D50:G50, dropping C8:G8, C47 and C50 (blank in GT). grader_guidance notes the exclusion. Local grade: GT passes, GT plus March-31 dates in C8:G8 and N/A/NM in C47/C50 now passes (was reg 0.9696), untouched input still fails.
- [F6](../findings.json) (Task Spec): "Fill in all empty cells" contradicts a GT that leaves row 8 and C47/C50 blank, and the strict regression check fails anyone who fills them
  - Change: Same answer_position change (C8:G8, C47, C50 no longer graded).
- other finding, critical, not in findings.json: Completing the labeled Period-End fields is penalized despite the instruction to fill empty cells
  - Change: Same answer_position change (Period-End C8:G8 no longer graded).
