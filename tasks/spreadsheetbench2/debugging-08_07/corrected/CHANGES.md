# Changes: SpreadsheetBench 2 debugging-08_07

Fix summary (from the fix record):

The answer key now also fixes the other real DCF errors QA named (R84 broken reference, negative C90 tax rate, ^5 terminal discounting, empty D&A links, capex linked to depreciation, hardcoded WACC). The earlier scope-limiting prompt sentence is removed, so the prompt is the original. Checked with the real SB2 scorer (original answer_position): new golden vs itself 1.0; input + all key fixes (26 cells, no cached values) 1.0; input + only the 5 planted INDEX/MATCH fixes 0.0 (mod 0.6827, 46 errors); untouched input 0.0.

Changed files (in this folder):

- reference/gt_08_golden.xlsx

## Fixed

- [F5](../findings.json) (Verification): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells fails all units (score 0.0) because fixing broken reference R84 (=R847-M83 -> =R83-M83) and negative tax rate C90 (-0.3 -> 0.3) alters modification cells C102/C107/C121/C135 against an incomplete golden file
  - Change: gt_08_golden.xlsx ('Operating Model + DCF') now also fixes the errors QA named, values recomputed with the verifier's LibreOffice recalc (21 cells changed, nothing else): R84 =R847-M83 -> =R83-M83; C90 -0.3 -> 0.3; C111, C125, C138 terminal value discounted ^5 -> ^6 (year 6 = 2030, matching H97/H99); C36:H36 D&A ='IS Annual'!C75:H75 (empty) -> =CFS!E4:J4 (FY2019-FY2024 D&A); I62:L62 capex ='IS Quarters'!E69:H69 (depreciation) -> =-'Key Stats'!G46:J46 (FY2025 quarterly capex, same sign convention as C62:H62); C98:H98 hardcoded WACC 0.0965997 -> ='Comps + WACC'!. C102/C107/C121/C135 now 2762.55.
- [F4](../findings.json) (Verification): Generic open-ended audit prompt contradicts narrow ground truth that only fixes 5 INDEX/MATCH formulas and leaves other genuine model bugs unfixed
  - Change: Same answer-key correction (R84, C90, C36:H36, I62:L62, C98:H98). Its other items are not errors: D11:H11 and I7:L7 are parts of multi-cell array formulas (C11:H11 {='IS Annual'!C11:H11}, I7:L7 {='IS Quarters 2'!D10:G10}), not hardcodes, and Comps + WACC!C29 using the relevered beta is the planted INDEX/MATCH fix itself.
- [F3](../findings.json) (Verification): Answer key keeps an obvious negative tax rate (C90 = -30%), so an agent that fixes it scores 0
  - Change: Same answer-key correction: C90 = 0.3 in the key.
- [F1](../findings.json) (Verification): Open-ended 'audit everything' instruction, but only 5 injected INDEX/MATCH fixes are graded and every other correct fix is penalized
  - Change: Same answer-key correction: C111, C125 and C138 discount the terminal value ^6; R84 and C90 fixed. The SG&A D11:H11 and I7 items are array-formula ranges, not hardcodes or broken refs (see F4).
- [F2](../findings.json) (Verification): Answer key preserves a broken working-capital reference and penalizes its correction
  - Change: Same answer-key correction: R84 =R83-M83 in the key.
