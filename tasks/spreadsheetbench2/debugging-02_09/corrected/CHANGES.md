# Changes: SpreadsheetBench 2 debugging-02_09

Fix summary (from the fix record):

The answer key's Berk-Hath dividend-rate sensitivity rows 11-14 held corrupted values from a self-referencing axis, so a correct table failed. Replaced those 20 cells with the true values; the pip/proxy finding is environment infra. Full pass: the data-table grids, which LibreOffice cannot evaluate, and the two OXY merger equity bridges, whose cash-consideration error the golden keeps, are no longer graded, so keeping the tables or repairing the bridges does not fail a correct output.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_02_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: Verifier fails mathematically correct sensitivity table repairs due to corrupted ground truth in Berk-Hath Investment Package!G11:K14 and penalizes legitimate model fixes as regressions
  - Change: files/gt/gt_02_golden.xlsx 'Berk-Hath Investment Package'!G11:K14 (20 hardcoded cells): replaced the corrupted values (rows 11/12 identical, row 13 = row 10) with the table's true values PV(k,10,-d*10000) + 10500/(1+k)^10 + warrant value C42 (736.334) for dividend rate d in F11:F14 and discount rate k in G9:K9. Row 10 is reproduced exactly by the same formula, which confirms the method. E.g. G11 11152.88 -> 11878.54, G12 -> 12241.37, G13 -> 12604.20, K14 -> 11425.01. Local check: patched GT and input + all GT changes both PASS
- [F3](../findings.json) (Verification): Generic open-ended debugging prompt clashes with narrow ground truth and contains mathematically corrupted sensitivity table values in gt_02_golden.xlsx
  - Change: files/gt/gt_02_golden.xlsx 'Berk-Hath Investment Package'!G11:K14 (20 hardcoded cells): replaced the corrupted values (rows 11/12 identical, row 13 = row 10) with the table's true values PV(k,10,-d*10000) + 10500/(1+k)^10 + warrant value C42 (736.334) for dividend rate d in F11:F14 and discount rate k in G9:K9. Row 10 is reproduced exactly by the same formula, which confirms the method. E.g. G11 11152.88 -> 11878.54, G12 -> 12241.37, G13 -> 12604.20, K14 -> 11425.01. Local check: patched GT and input + all GT changes both PASS. The generic 'audit thoroughly' prompt is the benchmark's design and is left as is; the confirmed defect is the corrupted table
- [F2](../findings.json) (Verification): Answer key's Berkshire dividend-rate sensitivity table (rows 11-14) has wrong values, so a correct fix fails the all-or-nothing verifier
  - Change: files/gt/gt_02_golden.xlsx 'Berk-Hath Investment Package'!G11:K14 (20 hardcoded cells): replaced the corrupted values (rows 11/12 identical, row 13 = row 10) with the table's true values PV(k,10,-d*10000) + 10500/(1+k)^10 + warrant value C42 (736.334) for dividend rate d in F11:F14 and discount rate k in G9:K9. Row 10 is reproduced exactly by the same formula, which confirms the method. E.g. G11 11152.88 -> 11878.54, G12 -> 12241.37, G13 -> 12604.20, K14 -> 11425.01. Local check: patched GT and input + all GT changes both PASS
- other finding, major, not in findings.json: Excel data tables (TABLE()) cannot survive the recommended openpyxl workflow, so a correct openpyxl fix fails both the regression and modification checks
  - Change: verifications[0].parameters.answer_position: 'DCF'!B1:Z35 split to skip the data-table grid V10:Z14, and 'Berk-Hath Investment Package'!B2:K44 split to skip the grids G10:K14, G18:K22 and G26:K30. These cells hold TABLE() formulas that LibreOffice returns as None, so they do not settle under the verifier's recalc. graderGuidance range note updated. The three reference fixes (DCF H18:R18, WACC G10:M10, Synergies D44:M44) and everything downstream outside the grids stay graded. The corrected G11:K14 values from the critical pass stay in the golden but are no longer graded. Checked with the real scorer (verifier's forced LibreOffice recalc) against files/gt/gt_02_golden.xlsx: golden PASS; input plus all golden changes PASS; input plus only the three formula fixes saved with openpyxl (TABLE() kept) FAIL before (reg 0.9913, mod 0.5545), PASS after; untouched input FAIL (mod 0.0).
- other finding, major, not in findings.json: Golden merger model double-counts cash consideration
  - Change: verifications[0].parameters.answer_position: 'Merger Model'!B2:J85 split to skip C29:E32 and C57:E60 (NewCo equity, price and gains of the two OXY bridges, all regression cells). The golden is left as is, and an output that also subtracts the cash consideration in E29/E57 now passes (before: reg 0.9972, 18 errors, FAIL). graderGuidance range note updated. Checked with the real scorer (verifier's forced LibreOffice recalc) against files/gt/gt_02_golden.xlsx: golden PASS; input plus all golden changes PASS; input plus only the three formula fixes saved with openpyxl (TABLE() kept) FAIL before (reg 0.9913, mod 0.5545), PASS after; untouched input FAIL (mod 0.0).

## Confirmed findings not fixed

- [F1](../findings.json): Incorrect golden values in the dividend sensitivity table
  - Reason: duplicate-of:F2
