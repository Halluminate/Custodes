# Changes: SpreadsheetBench 2 financial-model-03_03

Fix summary (from the fix record):

Full pass: seeded Equity_Table!D14 Net Income formula now adds associates, matching the key and the Income Statement.

Changed files (in this folder):

- reference/gt_03_Banking_golden.xlsx
- reference/untouched_input_03_03_Banking_input.xlsx
- inputs/03_03_Banking_input.xlsx

## Fixed

- other finding, major, not in findings.json: The seed's existing 2010 Net Income formula subtracts associates, but the answer key adds them
  - Change: 03_03_Banking_input.xlsx, untouched_input_03_03_Banking_input.xlsx and gt_03_Banking_golden.xlsx: Equity_Table!D14 formula =+D10-D11-D12-D13 changed to =+D10-D11-D12+D13 (XML edit, cached value unchanged because D13 = 0), so the seeded 2010 Net Income uses the same associates sign as the key's 2011-2016F cells and Income Statement row 31. Real scorer: golden 1.0, original golden as output against the patched key 1.0, untouched input 0.0 (modification 0).
- other finding, major, not in findings.json: Existing Net Income formula gives the opposite associates-income sign from the answer key
  - Change: Same change as another finding (not listed) (Equity_Table!D14 sign).
