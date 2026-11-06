# Changes: SpreadsheetBench 2 debugging-06_01

Fix summary (from the fix record):

The golden workbook 'fixed' Revenue Build!AC41/AC43 to an unprefixed '=rri(...)' that still evaluates to #NAME?, so a real CAGR fix failed. The golden now holds =_xlfn.RRI(5,W41,AA41) and =_xlfn.RRI(5,W43,AA43) with the computed CAGRs cached. Full pass: the key now also fixes the other model errors QA named (depreciation cohort references, Bear-case utilization row, PTA PV ranges, SGA startup row, J:L tax sign), with cached values recomputed only where those edits change them.

Changed files (in this folder):

- reference/gt_06_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells falsely rejects valid fixes to Revenue Build!AC41 and AC43 because gt_06_golden.xlsx expects #NAME? with unprefixed '=rri(...)'
  - Change: gt_06_golden.xlsx Revenue Build!AC41 = _xlfn.RRI(5,W41,AA41) (cached 0.379730) and AC43 = _xlfn.RRI(5,W43,AA43) (cached 0.718772), replacing '=rri(...)' cached #NAME?. Golden scores 1.0 locally; a #NAME? output now fails these two cells.
- [F1](../findings.json) (Verification): Golden workbook leaves #NAME? error in Revenue Build!AC41 and AC43 by writing '=rri(...)' without the OOXML '_xlfn.' prefix required by Excel and LibreOffice
  - Change: Same AC41/AC43 change in gt_06_golden.xlsx.
- [F3](../findings.json) (Verification): The ground truth keeps a #NAME? error in Revenue Build AC41/AC43, so the verifier fails both a correct fix and an untouched cell
  - Change: Same AC41/AC43 change in gt_06_golden.xlsx.
- [F2](../findings.json) (Verification): CAGR checks require broken formulas and reject correct numeric repairs
  - Change: Same AC41/AC43 change; equivalent fixes such as (AA41/W41)^(1/5)-1 now match on value.
- other finding, major, not in findings.json: Answer key preserves incorrect depreciation cohort references
  - Change: gt_06_golden.xlsx Supporting Schedules!J61:S70: the post-cohort branch '<prev col>$49/$E$57' -> 'HLOOKUP($B<row>,$J$46:$S$49,4,FALSE)/$E$57', so each capex cohort keeps depreciating its own year's capex (L61 1.333 -> 5). Cached values recomputed with the SB2 verifier's LibreOffice recalc, written only into formula cells (and the E61:E70 TRANSPOSE spill) whose value changes because of these edits (242 + 8 cells, e.g. Operating Model D&A/EBIT, DCF, Cover G10); one recalc settles. Scorer: golden 1.0/1.0, untouched input + all key changes 1.0/1.0, untouched input fails (mod 0.0).
- other finding, major, not in findings.json: Grader requires Base-case expenses despite the selected Bear case
  - Change: gt_06_golden.xlsx Supporting Schedules!O76:Y76: '-O80' (Base row) -> '-O77' (active-case row, as N76 already uses N77), e.g. O76 14.928 -> 16.794, S76 0 -> 11.818 under the selected Bear case. Cached values recomputed with the SB2 verifier's LibreOffice recalc, written only into formula cells (and the E61:E70 TRANSPOSE spill) whose value changes because of these edits (242 + 8 cells, e.g. Operating Model D&A/EBIT, DCF, Cover G10); one recalc settles. Scorer: golden 1.0/1.0, untouched input + all key changes 1.0/1.0, untouched input fails (mod 0.0).
- other finding, minor, not in findings.json: The golden leaves an inconsistent tax sign in Operating Model J25:L25
  - Change: gt_06_golden.xlsx Operating Model!J25:L25: '=IF(J23>0,$D$26*J23,0)' -> '=-IF(...)', matching M25:S25 (cached values stay 0, EBIT negative).
- other finding, major, not in findings.json: Open-ended 'audit and fix this file thoroughly' prompt conflicts with selective ground truth that only fixes 3 of the workbook's multiple broken formulas
  - Change: Answer key corrected for the errors this finding names: gt_06_golden.xlsx PTA!R22 =SUM('Operating Model'!O35:X35) -> J35:S35 (the forecast PV row used in DCF), PTA!R26 discount exponent 'Operating Model'!X34 (blank) -> S34. gt_06_golden.xlsx Supporting Schedules!F118:S118 =SUM(x112,x117) -> SUM(x112,x116,x117), adding the '(+) Startup Costs' row (changes H118/I118 only, forecast row 116 is 0). gt_06_golden.xlsx Supporting Schedules!O76:Y76: '-O80' (Base row) -> '-O77' (active-case row, as N76 already uses N77), e.g. O76 14.928 -> 16.794, S76 0 -> 11.818 under the selected Bear case. Cached values recomputed with the SB2 verifier's LibreOffice recalc, written only into formula cells (and the E61:E70 TRANSPOSE spill) whose value changes because of these edits (242 + 8 cells, e.g. Operating Model D&A/EBIT, DCF, Cover G10); one recalc settles. Scorer: golden 1.0/1.0, untouched input + all key changes 1.0/1.0, untouched input fails (mod 0.0).
- other finding, major, not in findings.json: Open-ended 'audit thoroughly' task is graded by all-or-nothing exact match on every downstream value
  - Change: Answer key now also fixes the other named model errors (depreciation cohorts, Bear-case utilization, PTA sums, SGA startup row, J:L tax sign), so a thorough audit is no longer failed for fixing them; see another finding (not listed)/another finding (not listed)/another finding (not listed)/another finding (not listed). The J34 stub-year is a valid convention and is left as is.
