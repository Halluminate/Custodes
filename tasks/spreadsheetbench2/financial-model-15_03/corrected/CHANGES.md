# Changes: SpreadsheetBench 2 financial-model-15_03

Fix summary (from the fix record):

Formats!B9 is =TODAY(), and B14:B16 (including the graded ATR cell B16) depend on it, so the golden itself fails on any date other than the day it was saved. I dropped Formats!B9 and B14:B16 from answer_position. Full pass: forecast Tangible assets (IS_BS_CF AC90/AH90/AM90/AR90) in the key now equal Gross Block minus Accumulated depreciation, the sheet's historical identity, instead of copying Gross Block.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_15_KIMS_golden.xlsx

## Fixed

- [F4](../findings.json) (Reward): SpreadsheetBench 2 official cell check: Golden workbook contains volatile =TODAY() in Formats!B9 causing verifier to fail when container clock differs from 2026-10-13
  - Change: verifications[0].parameters.answer_position: 'Formats'!A1:BT76 split so it skips Formats!B9 (=TODAY()) and the cells computed from it, B14 (months to target), B15 (years to target) and B16 (ATR). Locally the golden now scores regression 1.0, modification 1.0 (before: modification 0.9995, 3 errors), and the input with the golden's changes copied in also scores 1.0.
- [F3](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: verifications[0].parameters.answer_position: 'Formats'!A1:BT76 split so it skips Formats!B9 (=TODAY()) and the cells computed from it, B14 (months to target), B15 (years to target) and B16 (ATR). Locally the golden now scores regression 1.0, modification 1.0 (before: modification 0.9995, 3 errors), and the input with the golden's changes copied in also scores 1.0.
- [F2](../findings.json) (Reward): The ground truth fails its own verifier: a TODAY()-based cell in the graded range makes the binary check impossible to pass
  - Change: verifications[0].parameters.answer_position: 'Formats'!A1:BT76 split so it skips Formats!B9 (=TODAY()) and the cells computed from it, B14 (months to target), B15 (years to target) and B16 (ATR). Locally the golden now scores regression 1.0, modification 1.0 (before: modification 0.9995, 3 errors), and the input with the golden's changes copied in also scores 1.0.
- [F1](../findings.json) (Reward): The golden workbook fails its own grading because of a volatile date
  - Change: verifications[0].parameters.answer_position: 'Formats'!A1:BT76 split so it skips Formats!B9 (=TODAY()) and the cells computed from it, B14 (months to target), B15 (years to target) and B16 (ATR). Locally the golden now scores regression 1.0, modification 1.0 (before: modification 0.9995, 3 errors), and the input with the golden's changes copied in also scores 1.0.
- other finding, major, not in findings.json: Contradictory formula convention for Tangible Assets (row 90) vs. historical columns in IS_BS_CF
  - Change: ground_truth/gt_15_KIMS_golden.xlsx (XML edit on the original key, nothing else changed): IS_BS_CF!AC90, AH90, AM90, AR90 '=AC89' -> '=AC89-AC92' (same for AH/AM/AR), so forecast Tangible assets keep the sheet's own identity Gross Block = Tangible assets + Accumulated depreciation (B89:Z89 '=+B90+B92'). Cached values from the verifier's LibreOffice recalc: 29291.92/33291.92/37291.92/41291.92 -> 23273.8512/25396.336/27278.8208/28921.3056. No other cell references these four, and the recalc diff changed only them. Real SB2 scorer (answer_position from the critical fix): new key 1.0; input + all key changes 1.0; untouched input 0.0; the old key now fails only on these 4 cells.
- other finding, major, not in findings.json: GT forecast Tangible assets equals Gross Block, which breaks the model's historical Gross Block = Tangible + Accumulated Depreciation identity
  - Change: Same key edit as another finding (not listed) (AC90/AH90/AM90/AR90 = Gross Block - Accumulated depreciation).
