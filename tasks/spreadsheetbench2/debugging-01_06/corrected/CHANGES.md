# Changes: SpreadsheetBench 2 debugging-01_06

Fix summary (from the fix record):

The golden and reference workbooks carried stale cached values left by a corrupted data-table evaluation, so the golden file failed its own verifier. The caches now match the formulas, and the unreproducible data-table cells are dropped from answer_position. For the 'audit thoroughly' findings, the key now also fixes the Ex 5 Downside cohorts that used Upside acquisition counts, and the Ex 2 Multiple Expansion formula. The Ex 1 Upside/Downside case rows, which have no single repair, are no longer graded.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_01_golden.xlsx
- reference/untouched_input_Incorrect Cross Sheet References_input.xlsx
- inputs/Incorrect Cross Sheet References_input.xlsx

## Fixed

- [F4](../findings.json) (Verification): Golden gate: the ground-truth deliverable does not score full reward
  - Change: Recomputed the stale cached values: 65 formula cells in gt_01_golden.xlsx and 64 in untouched_input_Incorrect Cross Sheet References_input.xlsx (e.g. Ex 1 - LBO!C32 109.5182 -> 101.3452, C11 18.2034 -> 14.2034, U41 0.137 -> 0.092, Ex 2 - Valuation Bridge!C8 20567.08 -> 19673.94) now hold the values of their own formulas, taken from the verifier's own forced LibreOffice recalculation. Only <v> cached values were patched; formulas, styles and all other cells are byte-identical. The agent's data copy got the same 64 cache fixes so the input no longer shows numbers that contradict its formulas. verifications[0].parameters.answer_position: 'Ex 1 - LBO'!B1:AK95 split into runs that skip the 100 TABLE() cells in AG18:AK49. Their cached values are all the corrupted text '2.4x/19%', and the verifier freezes TABLE cells, so they cannot be reproduced by a correct workbook saved by openpyxl or LibreOffice. grader_guidance.md range note updated. Locally the patched golden, the golden re-saved by openpyxl without caches, both score 1.0 (before: regression 0.9938, modification 0.9362, 65 errors), and the untouched input scores 0.
- [F5](../findings.json) (Verification): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells is a trivial fail (false negative on Unit 1 and on ground truth) because it compares force-recalculated output against un-recalculated corrupted cached values in GT and input
  - Change: Same cache fix and answer_position change as gt-replay-0.
- [F1](../findings.json) (Verification): Uncorroborated cached values in ground truth (gt_01_golden.xlsx) and input (reference_path) due to corrupted LibreOffice TABLE() evaluation state cause the golden solution to fail verification
  - Change: Same cache fix and answer_position change as gt-replay-0.
- [F3](../findings.json) (Verification): Golden workbook's stale cached values do not match its own formulas, so the golden file fails its own verifier and the answer key cells (e.g., the non-reconciling valuation bridge) are graded on stale numbers
  - Change: Same cache fix and answer_position change as gt-replay-0.
- [F2](../findings.json) (Verification): Stale golden-workbook caches cause the answer key to fail its own verifier
  - Change: Same cache fix and answer_position change as gt-replay-0.
- other finding, major, not in findings.json: The answer key preserves incorrect M&A cohort references and penalizes their repair
  - Change: gt_01_golden.xlsx 'Ex 5 - M&A': Downside cohorts Z58:AB58, AA59:AB59 and AB60 now use the Downside counts $Z33/$AA33/$AB33 (they used Upside $S33/$T33/$U33). Cached values were rewritten only for the 20 Ex 5 cells whose LibreOffice-recalculated value changed (e.g. Z62 6.9 -> 0, AB62 37.03 -> 0, active block E58:G62 -> 0). No other cell changed. Checked with the real SB2 scorer: new key 1.0, input plus all key changes 1.0, untouched input 0.0, old key 0.0 (expected; it kept the Upside counts).
- other finding, major, not in findings.json: The open-ended 'audit thoroughly' instruction conflicts with an all-or-nothing grader that rewards only three specific fixes
  - Change: gt_01_golden.xlsx 'Ex 2 - Valuation Bridge'!C7 (Multiple Expansion) now =('Ex 1 - LBO'!AC18-'Ex 1 - LBO'!X18)*'Ex 1 - LBO'!AC17, multiplying by exit EBITDA instead of the exit multiple. The value stays 0 because entry and exit multiples are equal. The Upside/Downside rows of 'Ex 1 - LBO' (I19:M20, I24:M25, I29:M30, I34:M35) all point at the single Base PF P&L, and the workbook has no case-specific series for one defensible repair, so those 40 cells are left out of answer_position (verifier parameter and guidance). The other items named (X25 is numeric 0; Ex 4 F14 is the reported total with F13 as the plug) are not errors. Checked with the real SB2 scorer: new key 1.0, input plus all key changes 1.0, untouched input 0.0, old key 0.0 (expected; it kept the Upside counts).
