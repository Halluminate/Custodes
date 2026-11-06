# Changes: SpreadsheetBench 2 debugging-03_04

Fix summary (from the fix record):

The prompt asks for a thorough audit, but the key applied the Cover colour legend to only 9 cells. The key now also recolours the 368 cells QA named (LBO hard codes, C36, J62:N62, Valuation Bridge C3:C4, black hard codes in Ex 3, Ex 10 Forecast Assumptions and Ex 11), and these are graded. Named cells with no single legend colour (LBO F14/F21, Valuation Bridge C5:C7) and the remaining unnamed violations stay out of answer_position.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_03_golden.xlsx

## Fixed

- [F2](../findings.json) (Verification): Answer key recolours only 9 cells but leaves about 630 other colour-legend violations, so a thorough colour fix fails the regression check
  - Change: gt_03_golden.xlsx now also recolours the cells QA named to the Cover legend (font colour only, edited at the XML level; no values, formulas or other styles changed): LBO!J21:N21 and Q15:V15 hard codes black -> 0000FF; LBO!C36 (=SUM, a formula) blue -> 000000; LBO!J62:N62 same-sheet links black -> 7030A0; 'Valuation Bridge'!C3:C4 cross-sheet links black -> 00B050; the black numeric hard codes in 'Ex 3 - Balance Sheet' (90), 'Ex 11 - Multiples' (167) and 'Ex 10 - Forecast Assumptions ' (92) -> 0000FF. 368 cells in all; they are now graded again. Still left out of answer_position: LBO!F14, F21 and 'Valuation Bridge'!C5:C7 (named, but they mix cross-sheet links with arithmetic, so the legend gives no single colour: the model itself colours such cells green in C22 and black elsewhere), plus the earlier exclusion of the other, unnamed legend violations and ambiguous mixed formulas (282 cells, was 650). Checked with the real SB2 scorer (font_color mode): new key vs itself 1.0; untouched input plus the 9 planted and 368 named recolours 1.0; the golden with every violation recoloured to the legend 1.0; untouched input 0.0; planted-only recolouring (the old key) now fails (mod 0.0239), as expected.
- [F1](../findings.json) (Style): Golden color key penalizes compliance with the workbook's color legend
  - Change: gt_03_golden.xlsx now also recolours the cells QA named to the Cover legend (font colour only, edited at the XML level; no values, formulas or other styles changed): LBO!J21:N21 and Q15:V15 hard codes black -> 0000FF; LBO!C36 (=SUM, a formula) blue -> 000000; LBO!J62:N62 same-sheet links black -> 7030A0; 'Valuation Bridge'!C3:C4 cross-sheet links black -> 00B050; the black numeric hard codes in 'Ex 3 - Balance Sheet' (90), 'Ex 11 - Multiples' (167) and 'Ex 10 - Forecast Assumptions ' (92) -> 0000FF. 368 cells in all; they are now graded again. Still left out of answer_position: LBO!F14, F21 and 'Valuation Bridge'!C5:C7 (named, but they mix cross-sheet links with arithmetic, so the legend gives no single colour: the model itself colours such cells green in C22 and black elsewhere), plus the earlier exclusion of the other, unnamed legend violations and ambiguous mixed formulas (282 cells, was 650). Checked with the real SB2 scorer (font_color mode): new key vs itself 1.0; untouched input plus the 9 planted and 368 named recolours 1.0; the golden with every violation recoloured to the legend 1.0; untouched input 0.0; planted-only recolouring (the old key) now fails (mod 0.0239), as expected.
