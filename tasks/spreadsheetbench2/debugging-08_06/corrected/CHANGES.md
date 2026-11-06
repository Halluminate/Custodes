# Changes: SpreadsheetBench 2 debugging-08_06

Fix summary (from the fix record):

The answer key now also fixes every extra error QA named: the broken working-capital reference R84, the -30% tax rate in C90, the historical D&A link to an empty row (C36:H36), the FY2025 quarterly D&A shifted two quarters (I36:L36), and FY2025 quarterly capex taken from depreciation (I62:L62). Dependent values were recomputed. Grading parameters and prompt are unchanged.

Changed files (in this folder):

- reference/gt_08_golden.xlsx

## Fixed

- [F2](../findings.json) (Verification): Answer key retains a broken working-capital reference and penalizes its correction
  - Change: files/gt/gt_08_golden.xlsx: 'Operating Model + DCF'!R84 '=R847-M83' -> '=R83-M83' and C90 -0.3 -> 0.3 (unchanged from the earlier fix); dependents recomputed.
- [F3](../findings.json) (Verification): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check falsely fails all 3 units (score=0.0) for fixing genuine broken formulas left unfixed in gt_08_golden.xlsx
  - Change: files/gt/gt_08_golden.xlsx, 'Operating Model + DCF': besides R84 '=R847-M83' -> '=R83-M83' and C90 -0.3 -> 0.3, the key now also fixes C36:H36 D&A (pointed at empty 'IS Annual'!C75:H75) -> ='CFS'!E4..J4 (FY2019-FY2024 D&A, 70.248 ... 78.738), I36:L36 FY2025 quarterly D&A (two quarters early, 'IS Quarters'!E69:H69) -> ='IS Quarters'!G69..J69 (Q1-Q4 2025, matching the revenue link in row 4), and I62:L62 FY2025 quarterly capex (pointed at 'IS Quarters' depreciation) -> =-'Key Stats'!G21..J21 (quarterly capital expenditures, sum 44.85 = Key Stats I46). Dependent cached values recomputed with the verifier's LibreOffice recalc and written at XML level (48 cells, e.g. C92 33.2 -> 36.9, C93 33.2 -> 44.85, C116 277.17 -> 277.15). No other cell, formula or style changed.
- [F1](../findings.json) (Verification): Golden solution leaves blatant broken cell references and cross-sheet errors unfixed, penalizing thorough audits required by the prompt
  - Change: files/gt/gt_08_golden.xlsx, 'Operating Model + DCF': besides R84 '=R847-M83' -> '=R83-M83' and C90 -0.3 -> 0.3, the key now also fixes C36:H36 D&A (pointed at empty 'IS Annual'!C75:H75) -> ='CFS'!E4..J4 (FY2019-FY2024 D&A, 70.248 ... 78.738), I36:L36 FY2025 quarterly D&A (two quarters early, 'IS Quarters'!E69:H69) -> ='IS Quarters'!G69..J69 (Q1-Q4 2025, matching the revenue link in row 4), and I62:L62 FY2025 quarterly capex (pointed at 'IS Quarters' depreciation) -> =-'Key Stats'!G21..J21 (quarterly capital expenditures, sum 44.85 = Key Stats I46). Dependent cached values recomputed with the verifier's LibreOffice recalc and written at XML level (48 cells, e.g. C92 33.2 -> 36.9, C93 33.2 -> 44.85, C116 277.17 -> 277.15). No other cell, formula or style changed.
