# Changes: SpreadsheetBench 2 debugging-06_08

Fix summary (from the fix record):

The answer key now also fixes the named left-over model errors: historical D&A add-back on the D&A total row, cohort depreciation using each cohort's own capex, and the key's own tax-row sign slip. The pasted DCF sensitivity grids are no longer graded.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_06_golden.xlsx

## Fixed

- other finding, major, not in findings.json: The task asks for a thorough audit, but the ground truth only fixes sign errors and one beta average, and grading is all-or-nothing
  - Change: gt_06_golden.xlsx: Operating Model!H29 ='CFS Ann'!D19 -> ='CFS Ann'!D21 and I29 E19 -> E21 (175.5 -> 179.9, 201.7 -> 205.9), matching H7/H12, which use the D&A total row 21; cached values of dependents H32/I32 updated. J34 =0.75/2 already gives the correct 0.375, so values grading accepts a constant or a formula; no change. Checked with the real scorer (new answer_position): new golden 1.0; input + all key fixes saved with openpyxl (no caches) 1.0; old golden (planted fixes only) now 0.0 (mod 0.3682, expected); untouched input 0.0.
- other finding, minor, not in findings.json: The ground truth breaks the sign pattern of the tax row: J25:L25 lose the minus sign while M25:S25 keep it
  - Change: gt_06_golden.xlsx: Operating Model!J25:L25 restored to the input's =-IF(x23>0,$D$26*x23,0), the same sign as M25:S25 under '(-) Income Taxes'. Values stay 0 (EBIT negative).
- other finding, major, not in findings.json: Answer key retains a depreciation-vintage error that a thorough audit must fix
  - Change: gt_06_golden.xlsx: Supporting Schedules!J61:S70, the after-first-year branch now uses the cohort's own capex (row 61 $J$49, row 62 $K$49 ... row 70 $S$49) instead of the previous column's capex. Cached values recomputed with the verifier's LibreOffice recalc and injected at the XML level only where they moved (>1e-6): 165 formula cells downstream (Supporting Schedules rows 52/61-70 and E61:E70, Operating Model D&A/EBIT/NOPAT/UFCF/PV rows, DCF E3:J23 and M12/M30, Cover!G10, PTA!R22:R39). Operating Model!L12 273.20 -> 276.87. Checked with the real scorer (new answer_position): new golden 1.0; input + all key fixes saved with openpyxl (no caches) 1.0; old golden (planted fixes only) now 0.0 (mod 0.3682, expected); untouched input 0.0.
- other finding, major, not in findings.json: Grader requires incorrect hardcoded DCF sensitivity results to remain unchanged
  - Change: verifications[0].parameters.answer_position: 'DCF'!B2:AA50 split into 7 ranges that skip the sensitivity grids DCF!N13:Z25 and N31:Z43 (id, name, function, weight, mode unchanged). They are flattened data-table values, stale against the model, and the grading recalc cannot rebuild a data table, so there is no single gradeable correction; stale or refreshed grids now both pass. graderGuidance range text updated.
