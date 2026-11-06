# Changes: FINCH task-140

Fix summary (from the fix record):

The reference workbook deleted the input's F21 total and the whole 'NSS Combined Cashflows' table (U25:AA56), although the prompt says to preserve all original contents. Both are restored in gt_140_ref_0.xlsx from the input with their formulas, formatting and cached values.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_140_ref_0.xlsx

## Fixed

- [F1](../findings.json) (Verification): Ground truth deletes original table U25:AA56 and cell F21 despite prompt requiring preservation of all original contents
  - Change: gt_140_ref_0.xlsx 'Sheet1 (3)': F21 (=SUM(F7:F20)) and U25:AA56 (NSS Combined Cashflows, 184 non-empty cells) copied back from 140_src_0.xlsx with formats; cached values recomputed in LibreOffice and written in. All other cells, formulas, values and the 6 comments are unchanged.
- other finding, critical, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Same restore: the guidance grader marked the GT down for deleting original content; the reference now keeps it.
- other finding, major, not in findings.json: Undisclosed sign convention for P/L column (K7:K19 and K21: Prime minus Corporate vs. Corporate minus Prime)
  - Change: Grader guidance: task note accepts P/L as Prime cost minus Corporate cost (reference) or the reverse, applied consistently.
- other finding, major, not in findings.json: Task statement asks for an 'annual roll-up summary' (and mentions adding sheets) whereas GT only populates H21:K21 on the 13-month totals row
  - Change: Grader guidance: task note accepts the roll-up on the existing totals row or as an added summary (by calendar year or on a new sheet) that ties to the monthly rows, not counted as an over-edit.
- other finding, major, not in findings.json: The prompt never says how Carrying Cost and P/L are calculated, but the binary grader requires the reference's exact formulas
  - Change: Same task note on the P/L sign.
- other finding, major, not in findings.json: "Annual roll-up summary" is undefined, and the reference makes unrequested edits to the totals row
  - Change: Same task note on the annual roll-up; F21 already restored in the critical pass.
