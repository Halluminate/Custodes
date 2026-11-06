# Changes: SpreadsheetBench 2 financial-model-20_02

Fix summary (from the fix record):

The prompt named a sheet that does not exist ('Amortization / Fixed Assets'); that sentence now names 'Balance Sheet Schedules', where the annual amortization blanks are.

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, minor, not in findings.json: Instructions name a worksheet that does not exist
  - Change: problemStatement: one sentence changed, 'In the Amortization / Fixed Assets sheet, calculate annual amortization for FY24–FY27 by aggregating monthly values.' -> 'In the Balance Sheet Schedules sheet, calculate annual amortization ...'. The workbook has no such sheet; the annual blanks the key fills are 'Balance Sheet Schedules'!C23:F23. Nothing else in the prompt changed.
- other finding, minor, not in findings.json: The instruction names a sheet that does not exist ('Amortization / Fixed Assets') and misspells the real one
  - Change: Same sentence fix as another finding (not listed). The second sentence's spelling 'Balancesheet Schedules' is left as is: it plainly names the real sheet.
