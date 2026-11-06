# Changes: SpreadsheetBench 2 debugging-02_07

Fix summary (from the fix record):

The golden's dividend-rate sensitivity grid (Berk-Hath G11:K14) captured garbage from an Excel data table whose axis moved with its input, so a correct rebuild failed. The 20 cells now hold the values computed from the sheet's own inputs. Full pass: the intact TABLE() grids (and DCF V10) are no longer graded, and the key now also fixes the QA-named typos, the OXY merger equity bridges and Synergies Q17; Exhibit 9 N23:P23 left out.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_02_golden.xlsx

## Fixed

- [F3](../findings.json) (Verification): The ground truth's dividend-rate sensitivity grid (Berk-Hath G11:K14) is wrong, so a correct fix scores 0
  - Change: gt_02_golden.xlsx 'Berk-Hath Investment Package'!G11:K14 (20 hardcoded cells) recomputed as PV(disc,C14,-div*C11)+PV(disc,C14,0,-C17)+C42 for dividend rates F11:F14 (7.5%-9.0%) and discount rates G9:K9; e.g. G11 11,152.88 -> 11,878.54, G12 -> 12,241.37 (equals the golden's own term-table G20). Row 10 already matched this formula exactly. Golden scores 1.0 locally.
- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: Verifier fails valid sensitivity table fixes and all attempts due to corrupted ground-truth values in 'Berk-Hath Investment Package'!G10:K14
  - Change: Same G11:K14 recomputation in gt_02_golden.xlsx.
- [F2](../findings.json) (Verification): Corrupted ground-truth values in 'Berk-Hath Investment Package'!G10:K14 and un-recalculable TABLE() formulas in input make the sole verifier impossible to pass
  - Change: Same G11:K14 recomputation in gt_02_golden.xlsx.
- [F1](../findings.json) (Verification): Dividend sensitivity answer key contains incorrect graded values
  - Change: Same G11:K14 recomputation in gt_02_golden.xlsx.
- other finding, major, not in findings.json: Openpyxl breaks the workbook's data tables (TABLE() formulas), so an openpyxl edit fails the regression threshold even when nothing touches those tables
  - Change: verifications[0].parameters.answer_position (and the range list in graderGuidance): 'DCF'!B1:Z35 -> 'DCF'!B1:Z9,'DCF'!B10:U10,'DCF'!W10:Z10,'DCF'!B11:Z35 (drops the TABLE() corner V10) and 'Berk-Hath Investment Package'!B2:K44 split to skip the intact TABLE() grids G10:K14, G18:K22, G26:K30, which LibreOffice returns as None after an openpyxl save. The repaired DCF grid W10:Z14/V11:V14 stays graded. Real scorer (new answer_position, new key): golden PASS; untouched input plus every key change written by openpyxl PASS; the same with the Berk-Hath TABLE() grids kept PASS (old key/old range: FAIL reg 0.9912, None on V10 and the grids); previous key FAIL (24 errors on the new fixes); untouched input FAIL (mod 0.1957).
- other finding, major, not in findings.json: An open-ended 'audit and fix thoroughly' prompt is graded as an exact match on about 6,400 cells, so other valid fixes are rejected
  - Change: gt_02_golden.xlsx (on the critical-pass key, XML edit of three shared strings each used once): DCF!B3 'Value of Andarko ...' -> 'Value of Anadarko ...', Berk-Hath E4 'Senstivity' -> 'Sensitivity', WACC F17 'Commmon' -> 'Common'. The Berk-Hath data tables are covered by the another finding (not listed) range change; DCF I2 period-0 discounting has no single defensible repair and is not encoded. Real scorer (new answer_position, new key): golden PASS; untouched input plus every key change written by openpyxl PASS; the same with the Berk-Hath TABLE() grids kept PASS (old key/old range: FAIL reg 0.9912, None on V10 and the grids); previous key FAIL (24 errors on the new fixes); untouched input FAIL (mod 0.1957).
- other finding, major, not in findings.json: Golden workbook preserves material model errors that the requested thorough audit should fix
  - Change: gt_02_golden.xlsx (XML formula edits, cached values from one verifier LibreOffice recalc injected only into the changed cells and their dependents): Merger Model E29 =+E18+E23-E25-E26 -> ...-C10*C11 and E57 =E46+E51-E53-E54 -> ...-C38*C39 (NewCo equity net of the cash paid), so E31 and E59 = 25,367.95 = synergies less fees and costs; recached C29:E29, E30, C31:E31, C32:D32, C57:E57, E58, C59:E59, C60:D60. Synergies!Q17 =Q11*Q15 -> =Q16*Q15 (cash offer 16.25 x 504.3 = 8,194.875), recached Q17, Q19, Q24. answer_position: 'Exhibit 9'!A1:P30 -> A1:P22, A23:M23, A24:P30 (N23:P23 #REF! has no single defensible replacement). Real scorer (new answer_position, new key): golden PASS; untouched input plus every key change written by openpyxl PASS; the same with the Berk-Hath TABLE() grids kept PASS (old key/old range: FAIL reg 0.9912, None on V10 and the grids); previous key FAIL (24 errors on the new fixes); untouched input FAIL (mod 0.1957).
