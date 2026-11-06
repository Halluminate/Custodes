# Changes: SpreadsheetBench 2 debugging-04_03

Fix summary (from the fix record):

The prompt dated the restored restructuring charges one year earlier than the Fiscal Year columns where the golden places them, so following the prompt failed the all-or-nothing check. The prompt's year labels now use the model's Fiscal Year headers. The verifier's error-to-formula fallback that accepts a still-broken defined name is verifier code and is left as infra.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_04_golden.xlsx

## Fixed

- [F2](../findings.json) (Task Spec): Prompt reference data specifies wrong fiscal years (FY 2018 and FY 2019 instead of FY 2019 and FY 2020) for missing Income Statement line items, contradicting ground truth
  - Change: prompt.md reference-data line: year labels changed to the model's 'Fiscal Year' row 12 headers that the GT uses: '-$5.7M (FY ending 2019)' -> '(Fiscal Year 2020)', '-$0.6M (FY ending 2018)' -> '(Fiscal Year 2019)', '-$1.36M (FY ending 2019)' -> '(Fiscal Year 2020)'. GT Income Statement I29=-5.7, H30=-0.6, I30=-1.36 under headers H12=2019, I12=2020; no amounts changed.
- [F4](../findings.json) (Task Spec): The prompt's fiscal years for the restored line items are one year earlier than where the ground truth puts them
  - Change: Same prompt reference-data year-label change.
- [F1](../findings.json) (Task Spec): Historical charge dates contradict the graded answer
  - Change: Same prompt reference-data year-label change.
- other finding, major, not in findings.json: Open-ended instruction to 'audit and fix this file thoroughly' conflicts with pre-existing formula bugs preserved in gt_04_golden.xlsx
  - Change: files/gt/gt_04_golden.xlsx: 'PP&E, Debt, NWC'!C81:M83 now read the same-year Balance Sheet column (D17..N17, D29..N29, D30..N30); Total Debt Summary labels D65:H66 now ='Income Statement'!J11:N11 / J12:N12 (FY2021-2025, matching the D:H data); 'Income Statement'!J26:N26 =-'PP&E, Debt, NWC'!D73:H73 (was E73:I73, N26 a blank). 48 formula cells; cached values of the 306 dependent cells refreshed from the verifier's LibreOffice recalc (cells changing by >1e-6 only), nothing else touched. Real scorer (forced LibreOffice recalc): new key 1.0/1.0; untouched input fails (mod 0.0); the old key now fails (reg 0.984, mod 0.678). Two LibreOffice recalcs agree (0 cells differ), so the debt/interest loop settles.
- other finding, major, not in findings.json: Golden answer retains a shifted debt summary and incorrect projected interest
  - Change: Same key change (debt summary labels and IS J26:N26 interest alignment). Real scorer (forced LibreOffice recalc): new key 1.0/1.0; untouched input fails (mod 0.0); the old key now fails (reg 0.984, mod 0.678). Two LibreOffice recalcs agree (0 cells differ), so the debt/interest loop settles.
- other finding, major, not in findings.json: Golden working-capital calculations combine different fiscal years
  - Change: Same key change (NWC rows 81-83 same-year references). Real scorer (forced LibreOffice recalc): new key 1.0/1.0; untouched input fails (mod 0.0); the old key now fails (reg 0.984, mod 0.678). Two LibreOffice recalcs agree (0 cells differ), so the debt/interest loop settles.
- other finding, major, not in findings.json: Verifier enforces undisclosed row ordering and exact label constraints for restored rows in Control, Income Statement, and Cash Flow Statement
  - Change: answer_position (+ graderGuidance): left out the three placement/label choices with no single answer: Control!D5:E6 (Mil above or below Hun), 'Income Statement'!B29:J34 (order of the restored unusual-item rows; their totals stay graded in row 35), 'Cash Flow Statement'!B24 (exact capex label). Real scorer (forced LibreOffice recalc): new key 1.0/1.0; untouched input fails (mod 0.0); the old key now fails (reg 0.984, mod 0.678). Two LibreOffice recalcs agree (0 cells differ), so the debt/interest loop settles.

## Confirmed findings not fixed

- [F3](../findings.json): Verifier awards full credit with the broken defined name and hundreds of calculation errors
  - Reason: infra
