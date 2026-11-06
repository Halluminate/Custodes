# Changes: FINCH task-098

Fix summary (from the fix record):

Rebuilt the reference workbook from the source file so it keeps the original columns I:P, then filled only Sheet1 F:H with the reference's own dividend-yield and profit-growth values. Formula columns were recalculated.

Changed files (in this folder):

- prompt.md
- reference/gt_98_ref_0.xlsx

## Fixed

- [F2](../findings.json) (Verification): Ground truth workbook (gt_98_ref_0.xlsx) deletes Columns I through P of Sheet1 (35,427 cells), contradicting the task instruction to preserve all original contents
  - Change: gt_98_ref_0.xlsx is now 98_src_0.xlsx with Sheet1!F2:H5061 filled from the old reference (same values). Columns I:P (formulas and the Sharpe data) and Q:AB are back in their original positions; cached values recalculated in LibreOffice. Every other cell matches the source (checked cell by cell), Sheet2 unchanged.
- [F1](../findings.json) (Verification): The ground-truth workbook deletes original columns I–P, which breaks the task's own instruction to change nothing else
  - Change: Same rebuild: the reference no longer deletes source columns I:P or shifts Q:AB.
- other finding, critical, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: The low ground-truth grade came from the deleted columns; fixed by the same rebuild of gt_98_ref_0.xlsx.
- other finding, major, not in findings.json: Undisclosed metric definitions, calculation dates, and decimal vs. percentage-point scaling for Columns F, G, and H conflict with the grader's ±0.5 percentage point tolerance
  - Change: problemStatement: one added sentence stating the reference's conventions: decimals, single-quarter YoY growth in net profit attributable to the parent, 2025 Q2 and Q3 (checked against the key: 600519.SH G 0.0525 / H 0.0048 and 000001.SZ -0.0158 / -0.0275 are single-quarter attributable growth, not YTD).
- other finding, major, not in findings.json: Metric definitions and units are not stated, yet the ground truth uses one specific convention
  - Change: Same added prompt sentence (profit definition, single quarter, decimal units).
