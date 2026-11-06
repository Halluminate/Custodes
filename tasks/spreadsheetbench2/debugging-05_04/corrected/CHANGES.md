# Changes: SpreadsheetBench 2 debugging-05_04

Fix summary (from the fix record):

Key now also fixes the working-capital totals (Model rows 59 and 67 summed a days row and a % row), and the hardcoded forward-curve/Fed data cells, whose colour has no single right answer, are left out of the cell check.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_05_golden.xlsx

## Fixed

- other finding, major, not in findings.json: Grader requires preserving incorrect working-capital totals
  - Change: gt_05_golden.xlsx (XML formula edit of 20 cells): Model!E59:N59 'Total Current Assets' =SUM(E51:E53,E55,E57) -> =SUM(E51,E53,E55,E57) (drops row 52, Days Unbilled Outstanding) and E67:N67 'Total Current Liabilities' =SUM(E61:E63,E65) -> =SUM(E61,E63,E65) (drops row 62, a Net Revenue %); caches set from the SB2 LibreOffice recalc for the 33 cells whose value changed (rows 59, 67, 68 and F69:H69, e.g. E59 245.12 -> 137.738, E68 159.20 -> 51.887); stable on a second recalc; colours and all other cells untouched. Checked with the real scorer (font_color mode, new answer_position): new key 1.0; untouched input + the 7 key colour fixes + the 20 formula fixes 1.0; untouched input 0.0 (30 modification errors).
- other finding, major, not in findings.json: Hardcoded forward-curve data is left in black font, so applying the blue-input convention fails the whole task
  - Change: verifications[0].parameters.answer_position (and the same range list in graderGuidance): the hardcoded forward-curve and Fed data blocks, whose colour (black as in the key, or the model's input blue) has no single defensible answer, are left out: SOFR O10:Q130, 1-month and 3-month Term SOFR O10:P130, Fed Projections C9:G23 and B11:B23; titles and headers stay graded. Checked: input + key fixes with those 542 cells recoloured blue now scores 1.0 (0.9088 regression before); new key 1.0; untouched input fails.
