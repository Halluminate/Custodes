# Changes: SpreadsheetBench 2 debugging-06_04

Fix summary (from the fix record):

Two answer-key colors contradicted the Cover legend (WACC!C8 link black, Supporting Schedules!AD75 formula red); they are now green and black. The key now also fixes the calculation errors QA named: Operating Model!F20 pulled the amortization row instead of Other Operating Expense, and the capex-vintage depreciation rows used a rolling prior-year capex instead of each vintage's own capex. WACC!F10:F11 (assumption constants typed inside formulas) have no single correct repair and are no longer graded. Checked with the real SB2 scorer (font_color mode, new answer_position): new golden vs itself 1.0; input + all key fixes (values and the 28 colours, openpyxl, no cached values) 1.0; input + only the colour fixes 0.0 (mod 0.1634, 128 errors); untouched input 0.0.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_06_golden.xlsx

## Fixed

- [F2](../findings.json) (Style): Answer key colors changed cells against the Cover legend (e.g., WACC!C8 link set to black, Supporting Schedules!AD75 formula set to red)
  - Change: gt_06_golden.xlsx font colors only (new font+xf appended to styles.xml): WACC!C8 ='Comps + Beta'!C33 FF000000 -> FF00B050 (green, like the Operating Model J4:S4 / J14:S14 links); Supporting Schedules!AD75 =AVERAGE(F76:I76) FFFF0000 -> FF000000 (black, like DCF E9/E13/E16 formulas). Values unchanged; golden scores 1.0 locally.
- [F3](../findings.json) (Task Spec): Prompt asks for a full audit and fix, but grading checks only 28 font colors and penalizes most other legitimate fixes
  - Change: gt_06_golden.xlsx: Operating Model!F20 ='IS Ann'!C28 (Amortization of Goodwill, already inside CFS D&A) -> ='IS Ann'!C29 (Other Operating Expense, as G20:I20), so F20 = '-' and F21 = -434.9; Supporting Schedules J61:S70 vintage depreciation now uses each vintage's own capex after its first year (row 61 =IF(YEAR(K$9)<$B61,0,IF(YEAR(K$9)=$B61,K$49/$E$57/2,$J$49/$E$57)), row 62 $K$49, ... row 70 $S$49), e.g. L61 1.333 -> 5. 101 formula cells changed, fonts untouched, all cached values (incl. the E61:E70 TRANSPOSE array) recomputed with the verifier's LibreOffice recalc. WACC!F10 =F7*(0.3) and F11 =F8*0.4 have no single defensible repair (the 30%/40% haircuts are the modeller's assumptions; moving them to input cells or dropping them are both defensible), so verifications[0].answer_position skips WACC!F10:F11 ('WACC'!B2:F25 -> B2:F9, B10:E11, B12:F25) and the grader guidance range text matches.
- [F1](../findings.json) (Verification): Answer key penalizes formula repairs explicitly required by the audit
  - Change: Same answer-key correction as F3: the vintage depreciation rows (e.g. L61 = 150/30 = 5) are fixed in the key and all dependents recomputed.
