# Changes: SpreadsheetBench 2 template-14_07

Fix summary (from the fix record):

Row 16 vacant units relabelled and reconciled to Total minus Occupied (4,4,7,2) in input, untouched copy and golden; golden rows 19-20 updated.

Changed files (in this folder):

- reference/gt_14_07_golden.xlsx
- reference/untouched_input_14_07_input.xlsx
- inputs/14_07_input.xlsx

## Fixed

- other finding, major, not in findings.json: SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check fails runs that compute Vacancy Loss from Total Units minus Occupied Units
  - Change: Row 16 of RentRoll (the vacant-unit counts the GT's Vacancy Loss uses) is now consistent and labelled: B16 'FN: Express deductions as negative values' (a stray copy of the B22 footnote) became 'Vacant Units', and C16:F16 changed from 4, 3, 8, 1 to 4, 4, 7, 2 (= Total Units minus Occupied Units; G16 16 -> 17). Done in 14_07_input.xlsx, untouched_input_14_07_input.xlsx and gt_14_07_golden.xlsx at the XML level (sharedStrings + the four values); golden cached values for rows 19-20 updated (G19 -479,400 -> -514,200, G20 9,080,487 -> 9,045,687 = occupied units x leased rent x 12). Both readings (row 16 or Total minus Occupied) now give the same answer. SB2 scorer: new golden 1.0, input plus GT formulas 1.0, input plus Total-minus-Occupied formulas 1.0, untouched input fails (mod 0).
- other finding, major, not in findings.json: Corrupted row label in RentRoll!B16 and contradictory vacant unit counts create ambiguity in Vacancy Loss calculation
  - Change: Row 16 of RentRoll (the vacant-unit counts the GT's Vacancy Loss uses) is now consistent and labelled: B16 'FN: Express deductions as negative values' (a stray copy of the B22 footnote) became 'Vacant Units', and C16:F16 changed from 4, 3, 8, 1 to 4, 4, 7, 2 (= Total Units minus Occupied Units; G16 16 -> 17). Done in 14_07_input.xlsx, untouched_input_14_07_input.xlsx and gt_14_07_golden.xlsx at the XML level (sharedStrings + the four values); golden cached values for rows 19-20 updated (G19 -479,400 -> -514,200, G20 9,080,487 -> 9,045,687 = occupied units x leased rent x 12). Both readings (row 16 or Total minus Occupied) now give the same answer. SB2 scorer: new golden 1.0, input plus GT formulas 1.0, input plus Total-minus-Occupied formulas 1.0, untouched input fails (mod 0).
- other finding, major, not in findings.json: Row 16 has no label and its counts contradict Total Units minus Occupied Units, yet the GT's Vacancy Loss depends on it
  - Change: Row 16 of RentRoll (the vacant-unit counts the GT's Vacancy Loss uses) is now consistent and labelled: B16 'FN: Express deductions as negative values' (a stray copy of the B22 footnote) became 'Vacant Units', and C16:F16 changed from 4, 3, 8, 1 to 4, 4, 7, 2 (= Total Units minus Occupied Units; G16 16 -> 17). Done in 14_07_input.xlsx, untouched_input_14_07_input.xlsx and gt_14_07_golden.xlsx at the XML level (sharedStrings + the four values); golden cached values for rows 19-20 updated (G19 -479,400 -> -514,200, G20 9,080,487 -> 9,045,687 = occupied units x leased rent x 12). Both readings (row 16 or Total minus Occupied) now give the same answer. SB2 scorer: new golden 1.0, input plus GT formulas 1.0, input plus Total-minus-Occupied formulas 1.0, untouched input fails (mod 0).
- other finding, major, not in findings.json: Vacancy assumptions contradict total and occupied unit counts
  - Change: Row 16 of RentRoll (the vacant-unit counts the GT's Vacancy Loss uses) is now consistent and labelled: B16 'FN: Express deductions as negative values' (a stray copy of the B22 footnote) became 'Vacant Units', and C16:F16 changed from 4, 3, 8, 1 to 4, 4, 7, 2 (= Total Units minus Occupied Units; G16 16 -> 17). Done in 14_07_input.xlsx, untouched_input_14_07_input.xlsx and gt_14_07_golden.xlsx at the XML level (sharedStrings + the four values); golden cached values for rows 19-20 updated (G19 -479,400 -> -514,200, G20 9,080,487 -> 9,045,687 = occupied units x leased rent x 12). Both readings (row 16 or Total minus Occupied) now give the same answer. SB2 scorer: new golden 1.0, input plus GT formulas 1.0, input plus Total-minus-Occupied formulas 1.0, untouched input fails (mod 0).
- other finding, minor, not in findings.json: Footnote text is duplicated: one copy overwrites a row label, and the GT prints ### in its own render
  - Change: B16 no longer duplicates the footnote; it holds the row label 'Vacant Units' (same edit as above). The ### in the GT render is display width only and does not affect the cell check.
