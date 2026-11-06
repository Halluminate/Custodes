# Changes: SpreadsheetBench 2 debugging-08_08

Fix summary (from the fix record):

The answer key kept two real errors the 'audit and fix thoroughly' prompt asks the agent to fix: a -30% tax rate in DCF!C90 and the broken reference R84 '=R847-M83'. Both are corrected in the key and the DCF cells that depend on them were recomputed. Checked locally: the patched key scores 1.0 against itself and the input with all key fixes applied scores 1.0. Full pass: the key also fixes M27/R27, quarterly capex I62:L62, the TV discount exponent (^6) and Revenue Build J8; historical D&A C36:H36 and the NWC sign rows (D84:V84, C94:H94) are left out of answer_position so either sign convention passes.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_08_golden.xlsx

## Fixed

- [F5](../findings.json) (Verification): SpreadsheetBench 2 official cell check: Verifier penalizes valid fixes to 'Operating Model + DCF'!C90 and R84 due to unfixed errors in ground truth
  - Change: files/gt/gt_08_golden.xlsx: 'Operating Model + DCF'!C90 tax rate -0.3 -> 0.3 (matches D90:H90), and R84 '=R847-M83' -> '=R83-M83' (FY2026 change in NWC vs FY2025, like M84 and S84). Dependent cached values recomputed in LibreOffice (C91, C95, C100, C102, C107, C112, C114, C116, C118, C121, C126, C128, C130, C132, C135, C139, C141, C143, C145, D94, D95, D100, F107, F121). No other cell changed.
- [F3](../findings.json) (Verification): Golden solution leaves injected sign-convention and formula errors unfixed in 'Operating Model + DCF' (C90 = -0.3 and R84 = R847-M83)
  - Change: Same GT change as verifier-correctness-0 (C90 = 0.3, R84 = R83-M83, dependents recomputed).
- [F4](../findings.json) (Verification): Ground truth leaves an obvious broken cell reference (R84 =R847-M83) unfixed, and it feeds every valuation output
  - Change: Same GT change as verifier-correctness-0 (C90 = 0.3, R84 = R83-M83, dependents recomputed).
- [F2](../findings.json) (Verification): Ground truth keeps a negative tax rate (-30%) in the DCF bridge, a sign-convention error in a task named 'Incorrect Sign Conventions'
  - Change: Same GT change as verifier-correctness-0 (C90 = 0.3, R84 = R83-M83, dependents recomputed).
- [F1](../findings.json) (Verification): Answer key penalizes repairing a broken working-capital reference
  - Change: Same GT change as verifier-correctness-0 (C90 = 0.3, R84 = R83-M83, dependents recomputed).
- other finding, major, not in findings.json: Open-ended 'audit and fix thoroughly' prompt is graded all-or-nothing against one hidden set of fixes, and the GT leaves many other real defects in place
  - Change: Answer key gt_08_golden.xlsx now also fixes the further real errors QA named that have one defensible correction (XML edits, dependents recached with the verifier's LibreOffice recalc, no other cell changed): 'Operating Model + DCF'!M27 =M26/M7 -> =M26/M4 and R27 =R26/R7 -> =R26/R4 (% of revenue); I62:L62 quarterly capex ='IS Quarters'!E69:H69 (the depreciation row) -> =-'Key Stats'!G21:J21 (FY2025 quarterly capex, same sign convention as C62:H62; the four quarters sum to Key Stats I46 = 44.85, so M62 and C93 become 44.85); C111, C125, C138 terminal-value discount ^5 -> ^6 (TV sits at the end of year 6, H97 = 6); 'Revenue Build'!J8 264.758 -> 274.758 (the FY2024 data-centre quarters now sum to the annual M8 1,208.498 and J17 ties to 'IS Quarters'!D3 1,060.11). Historical D&A C36:H36 (='IS Annual'!C75:H75, a blank row, and IS Annual has no D&A line) has no single source, so C36:H36 is left out of answer_position; nothing else depends on it. Not changed: C89 =M20 is correct (M3 = 2025, M = FY2025 total), and N66/Q66 header formulas are value-neutral in values mode. Checked with the real scorer: new key 1.0 vs itself, input + all key changes 1.0, untouched input 0, an agent fixing only the previous key's set now fails (mod 0.8885).
- other finding, major, not in findings.json: Ambiguous sign convention for Change in Working Capital (Row 84 and Row 95) penalizes valid alternative DCF sign conventions
  - Change: answer_position: 'Operating Model + DCF'!A2:X145 split so D84:V84 (Change in NWC) and C94:H94 (its link into the bridge) are not graded; the UFCF row 95 and everything downstream still are. Either sign convention now passes as long as UFCF is right: checked a variant with R84:V84 = prior - current, M84 = H83-M83 and C95:H95 = ...+C94, which scores 1.0, like the key's own convention. graderGuidance range text updated.
- other finding, minor, not in findings.json: FY2024 revenue source data contains an unreconciled $10 million discrepancy
  - Change: Answer key 'Revenue Build'!J8 264.758 -> 274.758 (see another finding (not listed)): the only single-cell repair that makes the FY2024 data-centre quarters I8:L8 sum to the annual M8 and makes J17 tie to 'IS Quarters'!D3; J17 and the J22:J25 mix rows recached.
