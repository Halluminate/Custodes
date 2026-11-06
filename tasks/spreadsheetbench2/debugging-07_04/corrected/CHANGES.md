# Changes: SpreadsheetBench 2 debugging-07_04

Fix summary (from the fix record):

The answer key coloured 12 cross-sheet links black, Equity Returns!D5 an off-shade green, and kept 402 graded cells whose colour breaks the stated blue/green/black rule; all of them are now recoloured to the rule in the key (font only, XML level) and graded. Only the 12 typed-number formulas (no single correct colour) and the 38 circular 'LBO & Lenders' cells whose values drift under LibreOffice recalculation stay out of answer_position. Checked with the real SB2 scorer: new golden vs itself 1.0; input + every key fix (429 colours, openpyxl) 1.0; input + only the planted colour fixes 0.0 (mod 0.031); input + the previous key's fixes 0.0; untouched input 0.0.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_07_golden.xlsx

## Fixed

- [F8](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: gt_07_golden.xlsx recoloured (14 cells, see F6) and answer_position narrowed (see F3, F2). Local grade of the patched golden: regression 1.0, modification 1.0.
- [F9](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells trivially fails all runs (and fails the golden workbook itself) due to forced recalculation on unconverged circular references and contradictory golden font colors
  - Change: Golden recoloured (14 cells per F6, 402 per F3). verifications[0].parameters.answer_position drops only the 38 'LBO & Lenders' cells whose values do not settle under LibreOffice recalculation and the 12 typed-number formulas (was: also the 402 rule-breaking cells).
- [F7](../findings.json) (Verification): Golden workbook contradicts the stated font-color convention and fails its own verifier due to iterative calculation drift
  - Change: gt_07_golden.xlsx: 'Football Field'!E5,G5, 'LBO & Lenders'!S34:X34, 'Recapitalization'!E22:I22 font FF000000 -> FF00B050, 'Equity Returns'!D5 FF058005 -> FF00B050, and the remaining 402 rule-breaking cells recoloured to the rule (see F3); the circular LBO cells stay out of answer_position.
- [F2](../findings.json) (Reward): The answer key fails its own verifier: LBO circular-calculation cells cannot match after LibreOffice recalculation
  - Change: answer_position no longer includes the 'LBO & Lenders' cells whose values differ by more than 0.2% across LibreOffice recalculations of the golden, the input, or openpyxl-saved copies (S49:X59 loop, R35, R51, R62:R63, S37:X37, S45:X47, W28:W29).
- [F6](../findings.json) (Style): The answer key gives cells colours that contradict the stated blue/green/black rule
  - Change: gt_07_golden.xlsx: the 12 cross-sheet link cells ('Football Field'!E5,G5, 'Recapitalization'!E22:I22, 'LBO & Lenders'!S34:X34) recoloured from black to FF00B050, and 'Equity Returns'!D5 from FF058005 to FF00B050. Nothing else in the file changed (checked cell by cell).
- [F3](../findings.json) (Verification): Hundreds of cells in the answer key still break the stated colour rule, so a thorough correct fix fails the regression check
  - Change: gt_07_golden.xlsx: the 402 graded cells whose golden font colour broke the stated rule are now recoloured to the rule at XML level (new font+xf entries, values and formulas untouched): 189 purple 7030A0 and 151 blue 0000FF same-sheet formulas -> black 000000 (e.g. 'BS & CF'!F25 =-F49, 'DCF Model'!G11), 47 black hardcoded inputs -> blue 0000FF (e.g. 'DCF Model'!Q19, O29), 8 black and 6 purple cross-sheet formulas -> green 00B050 (e.g. 'LBO & Lenders'!S37), 1 green same-sheet formula ('DCF Model'!S7 =G127) -> black. These cells are graded again (the earlier exclusion is removed). The 12 formulas made only of typed numbers (e.g. 'DCF Model'!D37 =1925-40) have no single correct colour (input vs formula) and stay out of answer_position.
- [F1](../findings.json) (Style): Golden font colors contradict the task's explicit convention
  - Change: Same as F6 (golden cross-sheet links now green) and F3 (purple same-sheet formulas such as 'BS & CF'!F25 are now black in the key and graded).
- [F5](../findings.json) (Reward): Golden workbook fails its own mandatory recalculation and grading
  - Change: Same as F2: the circular debt-schedule cells (e.g. 'LBO & Lenders'!X53) are out of answer_position; patched golden through the forced-recalc path scores regression 1.0, modification 1.0.

## Confirmed findings not fixed

- [F4](../findings.json): Task prompt claims Pandas, openpyxl, and numpy are installed in the Python environment, but they are missing from the default python3
  - Reason: infra
