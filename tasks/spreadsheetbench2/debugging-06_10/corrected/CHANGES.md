# Changes: SpreadsheetBench 2 debugging-06_10

Fix summary (from the fix record):

The answer key changed the DCF stub period Operating Model!J34 from 0.75 to =0.75/2 while later years still add 1, which is no consistent convention, and nothing in the task asks for it. The key now keeps the input's 0.75, and the present values and valuation outputs that depend on it were recomputed. Checked locally: the patched key scores 1.0 against itself and the input with the key's real unit fixes applied scores 1.0.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_06_golden.xlsx

## Fixed

- [F1](../findings.json) (Verification): Answer key uses a broken discount-period convention: the stub period is halved but later periods still step by +1
  - Change: files/gt/gt_06_golden.xlsx: 'Operating Model'!J34 '=0.75/2' -> 0.75 (same as the input), so K34:S34 become 1.75 ... 9.75. Cached values recomputed in LibreOffice for Operating Model J34:S35, DCF E3, E7, E9, E13, E16, E22, E23, J3, J7, J9, J13, J16, J22, J23, M12, M30, Cover!G10 and PTA R22, R28, R32, R35, R38, R39. No other cell changed.
- other finding, major, not in findings.json: GT keeps obvious errors in graded cells, so an agent that fixes them fails the all-or-nothing check
  - Change: gt_06_golden.xlsx (on top of the prepared J34 fix): PTA!R22 =SUM('Operating Model'!J35:S35) (was O35:X35); DCF!J23 =J6/'Operating Model'!S23 (TV / terminal EBIT, was J7 PV of TV); DCF!E23 =(E4*E6-'Operating Model'!S32)/('Operating Model'!S32+DCF!E6) (undiscounted final FCF, was S35). PTA!R24 (Median EV/EBIT Multiple) is blank and the sheet has no EV/EBIT data to fill it, so there is no single repair: answer_position leaves out PTA R24:R26 and their dependents R28, R32, R35, R38, R39 ('PTA'!B2:R39 split); grader guidance range text updated. 40 formula cells changed, 171 dependent cached values (incl. the E63:E70 TRANSPOSE members) taken from the verifier's LibreOffice recalc; nothing else changed. Checked with the real SB2 scorer (new answer_position): new key vs itself PASS (reg 1.0, mod 1.0), input plus all key changes (formulas only, no cached values) PASS, untouched input FAIL (mod 0.0).
- other finding, major, not in findings.json: Open-ended 'audit everything' prompt graded by binary exact match against one particular set of fixes
  - Change: gt_06_golden.xlsx: 'Supporting Schedules'!K20 264 -> =J20 (same as L20:S20), so K20 carries 264.35 and its dependents are recomputed. The open-ended audit prompt is the benchmark's design and is unchanged. 40 formula cells changed, 171 dependent cached values (incl. the E63:E70 TRANSPOSE members) taken from the verifier's LibreOffice recalc; nothing else changed. Checked with the real SB2 scorer (new answer_position): new key vs itself PASS (reg 1.0, mod 1.0), input plus all key changes (formulas only, no cached values) PASS, untouched input FAIL (mod 0.0).
- other finding, major, not in findings.json: Golden workbook preserves depreciation errors that a thorough audit must fix
  - Change: gt_06_golden.xlsx 'Supporting Schedules': the 36 full-year cells of rows 61-68 (from two columns after each vintage year, e.g. L61:S61, M62:S62 ... S68) now use their own vintage's capex: =IF(YEAR(L$9)<$B61,0,IF(YEAR(L$9)=$B61,L$49/$E$57/2,$J$49/$E$57)) ... $Q$49 for row 68 (L61 1.333 -> 5). Same correction as the sibling key for this golden. 40 formula cells changed, 171 dependent cached values (incl. the E63:E70 TRANSPOSE members) taken from the verifier's LibreOffice recalc; nothing else changed. Checked with the real SB2 scorer (new answer_position): new key vs itself PASS (reg 1.0, mod 1.0), input plus all key changes (formulas only, no cached values) PASS, untouched input FAIL (mod 0.0).
