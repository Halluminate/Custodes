# Changes: SpreadsheetBench 2 debugging-04_05

Fix summary (from the fix record):

The answer key now also fixes the other real errors QA named in graded cells (ROA averaging windows, debt/net worth and PP&E/sales column offsets, the one-year interest shift, the inconsistent projection averages and the mixed-year working-capital rows), with all values recomputed. The earlier scope-limiting prompt sentence and the Line Item Metrics H24:I24 grading exclusion are removed, so the prompt, guidance and answer_position are the originals. Checked with the real SB2 scorer: Real SB2 scorer, original answer_position: new golden vs itself 1.0; input + every key fix (103 cells, no cached values) 1.0; input + only the planted AVERAGE fixes (old key) 0.0 (mod 0.1587, 216 errors); untouched input 0.0 (mod 0.0).

Changed files (in this folder):

- reference/gt_04_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): Ground-truth workbook gt_04_golden.xlsx leaves multiple genuine formula and AVERAGE errors unfixed inside graded ranges, penalizing thorough fixes
  - Change: gt_04_golden.xlsx now also fixes the errors QA named (93 formula cells, all cached values recomputed with the verifier's LibreOffice recalc): Line Item Metrics H24:M24 ROA averages the prior and current year's total assets (H24 =H14/AVERAGE('Balance Sheet'!H27:I27), I24 I27:J27, ... M24 M27:N27); Line Item Metrics C27:H27 debt/net worth now read the same year's Balance Sheet column (D:I instead of C:H); Line Item Metrics H35:M35 net PP&E now read Balance Sheet I:N instead of J:O; Income Statement J26:N26 interest now links to the same year, =-'PP&E, Debt, NWC'!D73 ... H73 (was E73 ... blank I73); Income Statement K45:N49 and Balance Sheet K70:N70, K72:N72, K74:N74 now average all six historical years : like column J (were :), and Balance Sheet J71:N71 =AVERAGE(:) (was a rolling window that pulled in projections); 'PP&E, Debt, NWC' C81:M83 inventory, payables and accrued expenses now read the same year as receivables (Balance Sheet D:N instead of C:M).
- [F2](../findings.json) (Verification): The prompt asks for a thorough audit, but the grader only accepts the two injected AVERAGE fixes, and the answer key leaves other real errors in graded cells unfixed
  - Change: Same answer-key correction as F4: H24/I24 ROA windows, row 27 column offsets, Income Statement J45:N49 and Balance Sheet J70:N74 averages now consistent.
- [F1](../findings.json) (Verification): Answer key preserves a one-year shift in projected interest expense
  - Change: Same answer-key correction as F4: Income Statement J26:N26 = -'PP&E, Debt, NWC'!D73:H73 (2021-2025 interest), so N26 is no longer 0 and Line Item Metrics M29 is no longer #DIV/0!.
- [F3](../findings.json) (Verification): Golden working-capital schedule mixes current-year receivables with prior-year balances
  - Change: Same answer-key correction as F4: 'PP&E, Debt, NWC' C81:M83 read the same-year Balance Sheet columns; DCF!C19 is now -21.65 (was 22.31).
