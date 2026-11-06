# Changes: SpreadsheetBench 2 debugging-10_01

Fix summary (from the fix record):

The model's cash/revolver loop (Model!I195 feeds back on I182 with slope -1) oscillates under iterative calculation and never converges, so the golden values depend on the engine and the iteration count. Even the answer key scores 0 after the forced LibreOffice recalc. The check now compares formulas instead of values: the answer key and an input with exactly the 9 double-counting fixes both score 1.0, and the 5 Model!I45:M45 fixes that values mode could not see are now graded. Full pass: the key also fixes the further QA-named errors with one defensible correction (16 cells); #REF! cells and unreconciled historical cash-flow figures are left out of answer_position.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_10_golden.xlsx

## Fixed

- [F5](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells fails all units (including exact 9-formula golden solutions in Units 1 and 3 and the ground truth itself) due to LibreOffice vs Excel circular-reference recalculation divergence
  - Change: verifications[0].parameters.mode: 'values' -> 'formula' (id, name, function, weight, answer_position unchanged). Locally, with the verifier's forced-recalc profile, gt_10_golden.xlsx scores regression 1.0 / modification 1.0, and the untouched input with only the 9 GT formula edits applied also scores 1.0/1.0. grader_guidance.md comparison text updated to match.
- [F1](../findings.json) (Reward): Golden workbook fails its own values-mode verifier due to an unfixed oscillating circular reference, and values mode misses 5 of the 9 double-counting formula fixes
  - Change: Same mode change. Formula mode grades all 9 fixes (Model I45:M45, I112, I164, P&L Summary G13, G32), including the 5 I45:M45 fixes whose values are identical in the Base Case, and no longer depends on the oscillating loop's values.
- [F3](../findings.json) (Reward): The ground-truth file fails its own grading: after the LibreOffice recalc the verifier forces, the GT scores only 29% on the cells it changed
  - Change: Same mode change; the GT now passes its own check.
- [F2](../findings.json) (Reward): The golden workbook fails its own grading after mandatory recalculation
  - Change: Same mode change.
- [F4](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: Same mode change; GT replay locally scores 1.0.
- other finding, major, not in findings.json: Generic task prompt asks to fix hardcoded values and broken cell references, but the golden workbook only fixes double-counting formulas and penalizes fixing other real errors
  - Change: gt_10_golden.xlsx (XML edits on the original key; only these cells changed; cached values of edited cells set to their direct result or kept, nothing else recalculated): Model!H43 0.1 -> =SUM($F43,G43) (FY26E like H41/H47/H52); Model!K57:M57 0.112/0.11/0.108 -> =CHOOSE($C$2,S57,AA57,AI57) etc. (row pattern of G57:J57; Base Case 0.113/0.11/0.107); Model!I195:M195 and I205:M205 cash-sweep term (I$182-$K$11) -> (I$180-$K$11) (beginning cash, removes the self-referencing loop); label 'Payrol Syn.' -> 'Payroll Syn.' (shared string used by Model!B102 and 'P&L Summary'!B28). answer_position (id/name/function/weight/mode unchanged; graderGuidance range list updated): named errors with no single defensible correction are no longer compared: the 33 '=#REF!' cells ('FY2024A (Earnings)'!C5:N5, 'FY2027P (IS)'!K33:N33, 'FY2027P (Earnings)'!A1, 'FY2028P (IS)'!A3:A4, C9, L9, C33:N33; the lost targets cannot be recovered). Local SB2 grade (formula mode, new ranges): patched GT 1.0/1.0; untouched input + the 9 planted fixes + these 16 cells 1.0/1.0. Untouched input fails (mod 0.0, 25 cells); the previous key now fails on exactly the 16 new cells.
- other finding, major, not in findings.json: The prompt asks for an open-ended thorough audit, but the grader requires an exact match to a GT that changes only 9 formulas
  - Change: Same key edits for the named K57:M57 hardcodes and the 'Payrol' label typo (see another finding (not listed)). J239/K239:M239 and J246 are lease step-up inputs, not errors, and are unchanged.
- other finding, minor, not in findings.json: Historical cash-flow sources and the golden baseline do not reconcile
  - Change: answer_position: 'FY2023A (CF)'!C40:C45, C48, N55:O55 and 'FY2025A (CF)'!N33:N34, N37 are no longer compared (hardcoded source figures that do not reconcile, with no way to tell which side is wrong). Key unchanged.
