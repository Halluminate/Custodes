# Changes: SpreadsheetBench 2 financial-model-15_02

Fix summary (from the fix record):

Fixed the golden's group totals from 4QFY24 onward so they include State 8, matching the golden's own revenue (row 7) and EBITDA (row 9) totals. The prompt now says the revenue mix covers every quarter and year and names the revenue row each ratio divides by, as the key does.

Changed files (in this folder):

- prompt.md
- reference/gt_15_KIMS_golden.xlsx

## Fixed

- [F2](../findings.json) (Verification): Answer key leaves State 8 out of the group totals in rows 40-50 from 1QFY25 onwards
  - Change: Golden gt_15_KIMS_golden.xlsx: added State 8 (rows 178-187) to the seven-state group-total formulas in 'Work Sheet' rows 40-44, 47 and 49 for columns Z:AF, e.g. AB40 '=AB59+...+AB161+AB178'. AG:AP already had it. Cached values come from a LibreOffice recalculation and were written into only the affected Work Sheet cells: AB40 4702 -> 5002, AB47 6819.80 -> 6884.60 (now equal to AB7), AB49 1856.63 -> 1859.87 (now equal to AB9), with dependents in rows 45, 46, 48 and 50. The volatile TODAY() cells in Formats keep their original caches. The golden grades 1.0 locally.
- [F1](../findings.json) (Verification): Answer key omits State 8 from FY25 group totals
  - Change: Golden gt_15_KIMS_golden.xlsx: added State 8 (rows 178-187) to the seven-state group-total formulas in 'Work Sheet' rows 40-44, 47 and 49 for columns Z:AF, e.g. AB40 '=AB59+...+AB161+AB178'. AG:AP already had it. Cached values come from a LibreOffice recalculation and were written into only the affected Work Sheet cells: AB40 4702 -> 5002, AB47 6819.80 -> 6884.60 (now equal to AB7), AB49 1856.63 -> 1859.87 (now equal to AB9), with dependents in rows 45, 46, 48 and 50. The volatile TODAY() cells in Formats keep their original caches. The golden grades 1.0 locally.
- other finding, major, not in findings.json: 'For all years' revenue-mix scope does not match the answer key, which also fills quarterly columns
  - Change: Prompt: 'calculate for all years the % of total revenue mix' now reads 'calculate for all quarters and years the % of total revenue mix (...)', matching the key, which fills rows 25-31 in every quarterly and FY column that has state revenue (e.g. T25 =T15/T$7).
- other finding, major, not in findings.json: Revenue mix and EBITDAM use different, unstated revenue denominators that differ by more than the 1% tolerance
  - Change: Prompt now names the denominators the key uses: the revenue mix is each state's revenue over Total Revenues (inc. Other Income) (row 7, e.g. Q25 =Q15/Q$7), and EBITDAM (calc) is EBITDA (calc) over Total Revenues (row 5, e.g. V10 =V9/V5). The two rows differ by more than the 1% tolerance, and the prompt named neither. Key unchanged.
