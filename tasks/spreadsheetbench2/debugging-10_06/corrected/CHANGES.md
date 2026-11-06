# Changes: SpreadsheetBench 2 debugging-10_06

Fix summary (from the fix record):

The answer key is rebuilt from the original golden at XML level (the earlier version was a full LibreOffice re-save, which also rewrote every other cell, dropped the charts and turned the =#REF! cells into =#ref!). It now fixes the errors QA named: Model!D169 CapEx sign, Model!F218 applying the Beloeil lease flag  twice, and Model!I195:M195 ABL paydown using ending instead of beginning cash; only their dependents' cached values were recomputed with the verifier's LibreOffice recalc, plus the 84 '4-Wall Analysis' location labels whose Excel-cached text (line break) differs from the recalculated text. The 33 literal =#REF! cells QA named have no recoverable reference, so they are left out of answer_position, as are the circular cash/debt cells already excluded. Checked with the real SB2 scorer (new answer_position): new golden vs itself 1.0; input + all key fixes (10 cells, no cached values) 1.0; input + only the 3 planted fixes 0.0 (mod 0.9202, 368 errors); untouched input 0.0 (mod 0.0009).

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_10_golden.xlsx

## Fixed

- [F7](../findings.json) (Reward): SpreadsheetBench 2 official cell check: `verify_spreadsheetbench2_cells` scores 0.0 on all runs and on the golden workbook itself due to LibreOffice-vs-Excel circular reference divergence and unfixed `Model!D169`
  - Change: gt_10_golden.xlsx rebuilt from the original: Model!D169 ='FY2024A (CF)'!O37/Mil -> =-'FY2024A (CF)'!O37/Mil (as C169, E169, F169); dependents' cached values recomputed (Model, P&L Summary; 523+32 cells). answer_position keeps the existing exclusion of the cells in or downstream of the iterative cash/debt loop (Model I:M rows 121-207, AV:AX rows 20-43, P&L Summary R7:T8, G40:K41).
- [F6](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: The rebuilt golden scores 1.0 on the cell check: same D169 fix and loop-cell exclusion, and the 84 '4-Wall Analysis' label formulas (e.g. BS5 =R4) whose cached text 'Beloeil,
Quebec' fails against the recalculated 'Beloeil, Quebec' now carry the recalculated text.
- [F2](../findings.json) (Verification): Golden ground-truth workbook fails its own verifier under LibreOffice recalculation and leaves a broken cross-sheet sign reference (`Model!D169`) unfixed
  - Change: D169 sign fixed in the golden; golden passes its own check (see gt-replay-0).
- [F4](../findings.json) (Verification): Broad 'audit and fix this file thoroughly' prompt conflicts with exact-cell grading that only expects 3 undisclosed edits and environment lacks advertised Python packages
  - Change: Key now also fixes the named Model!F218 =(0.5*(843375))/1000000*$C$310 -> =(0.5*(843375))/1000000 (F220 already multiplies by C310; value unchanged while the flag is 1) and Model!I195:M195 paydown (I$182-$K$11) -> (I180-$K$11) (beginning cash). The 33 literal =#REF! cells it names ('FY2024A (Earnings)'!C5:N5, 'FY2027P (IS)'!K33:N33, 'FY2027P (Earnings)'!A1, 'FY2028P (IS)'!A3:A4, C9, L9, C33:N33) have no single defensible repair (the deleted references cannot be recovered), so verifications[0].answer_position now skips them; grader guidance range text matches. The missing openpyxl is an environment issue, not changed here.
- [F3](../findings.json) (Reward): The ground-truth workbook fails its own verifier after LibreOffice recalculates it, so no output can pass
  - Change: Unconverged circular cells stay out of answer_position (existing exclusion); golden passes its own check.
- [F1](../findings.json) (Reward): Golden workbook fails its own forced-recalculation grading
  - Change: Same as F3.
- [F5](../findings.json) (Verification): Answer key penalizes a formula correction explicitly required by the audit
  - Change: Model!D169 is =-'FY2024A (CF)'!O37/Mil in the key, so D134/D137 match a correct fix.
