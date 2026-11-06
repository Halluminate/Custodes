# Changes: SpreadsheetBench 2 debugging-04_01

Fix summary (from the fix record):

The answer key fixed only the 3 planted rows and kept real year-shift errors, so a thorough audit scored 0. The golden now also fixes the interest and working-capital links and the named 'Line Item Metrics' ROA (H24:M24) and PP&E-to-sales (H35:M35) shifts, recalculated with the verifier's LibreOffice. 'Line Item Metrics'!I27 and 'Balance Sheet'!J71 have no single defensible repair and are not graded. The earlier scope sentence in the prompt is removed.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_04_golden.xlsx

## Fixed

- [F1](../findings.json) (Verification): Broad audit instruction conflicts with golden workbook that preserves broken formulas/references (#DIV/0! and off-by-one shifts) and includes an unannounced non-double-counting LBO edit
  - Change: gt_04_golden.xlsx: 'Income Statement'!J26:N26 now =-'PP&E, Debt, NWC'!D73..H73 (was E73..I73: 2022 interest booked in 2021, 2025 interest 0) and 'PP&E, Debt, NWC'!C81:M83 now ='Balance Sheet'!D..N rows 17/29/30 (was C..M, prior-year inventory/payables/accruals against same-year receivables); recalculated through the grader's LibreOffice path (293 dependent values moved, e.g. Summary!H12 57.968 -> 58.593, H13 0.2400 -> 0.2533, matching the thorough runs). Patched golden grades regression 1.0, modification 1.0 locally. Audit rework: the prompt sentence 'Leave the model's forecast assumptions and hardcoded inputs as they are.' is removed (prompt back to the original). gt_04_golden.xlsx now also fixes the named 'Line Item Metrics' year shifts, every other cell unchanged and 12 cached values rewritten from the verifier's LibreOffice recalc: H24:M24 ROA now averages 'Balance Sheet' total assets of the prior and current year (H27:I27 ... M27:N27, as C24:G24 do; were H27:J27, J27:K27 ...), and H35:M35 Net PP&E to Sales use the same-year 'Balance Sheet' column (I22 ... N22, as C35:G35 do; were J22 ... O22). H24, I24, H35 and I35 are graded again. Left out of answer_position because there is no single defensible repair: 'Line Item Metrics'!I27 (named in I27:M27, but I27 already reads the same-year 'Balance Sheet' column J), and 'Balance Sheet'!J71 (the named rolling averages J71:N71: rows 70, 72 and 74 use AVERAGE($D:$I) in J but AVERAGE($D:$H) in K:N, so neither pattern is clearly right; J71's value is the same either way, and only J is graded). C27:H27 are graded as in the original task. Checked with the real SB2 scorer: new key vs itself 1.0; untouched input plus all key fixes 1.0; untouched input 0.0; the previous key (without the Line Item Metrics fixes) now fails (mod 0.9796), as expected.
- [F2](../findings.json) (Verification): Answer key preserves misaligned financial-year references and penalizes valid audit repairs
  - Change: gt_04_golden.xlsx: 'Income Statement'!J26:N26 now =-'PP&E, Debt, NWC'!D73..H73 (was E73..I73: 2022 interest booked in 2021, 2025 interest 0) and 'PP&E, Debt, NWC'!C81:M83 now ='Balance Sheet'!D..N rows 17/29/30 (was C..M, prior-year inventory/payables/accruals against same-year receivables); recalculated through the grader's LibreOffice path (293 dependent values moved, e.g. Summary!H12 57.968 -> 58.593, H13 0.2400 -> 0.2533, matching the thorough runs). Patched golden grades regression 1.0, modification 1.0 locally.
