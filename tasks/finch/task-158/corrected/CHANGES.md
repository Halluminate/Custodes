# Changes: FINCH task-158

Fix summary (from the fix record):

The reference workbook changed a hardcoded input (OCT 01!T38 16 -> 18) and dropped a row-total formula, neither supported by the task. I restored both in the reference so it differs from the source only by the T39 formula fix.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_158_ref_0.xlsx

## Fixed

- [F2](../findings.json) (Environment & Infra): Source workbook 158_src_0.xlsx has a corrupted static input in OCT 01!T38 (16 vs 18.0 in GT) and an extra formula in OCT 01!V30, so fixing the formula error in OCT 01!T39 still fails to match ground-truth values
  - Change: gt_158_ref_0.xlsx, sheet 'OCT 01': restored the source input T38 = 16 (reference had an unexplained 18.0) and the source row-total formula V30 '=SUM(D30:T30)' (reference had blanked it). The only intended change, the T39 formula fix '=SUM(T6:T36)+T38', is kept. Cached values refreshed: T39 -12037, T40 132734, V38 5804, V39 131971, V40 161441, V30 0; no other cell changed.
- [F1](../findings.json) (Verification): Answer key hardcodes a new value in OCT 01!T38 (16 → 18) with nothing in the materials pointing to it
  - Change: gt_158_ref_0.xlsx, sheet 'OCT 01': restored the source input T38 = 16 (reference had an unexplained 18.0) and the source row-total formula V30 '=SUM(D30:T30)' (reference had blanked it). The only intended change, the T39 formula fix '=SUM(T6:T36)+T38', is kept. Cached values refreshed: T39 -12037, T40 132734, V38 5804, V39 131971, V40 161441, V30 0; no other cell changed.
- other finding, major, not in findings.json: Broad workbook-wide audit prompt conflicts with unfixed formula errors in gt_158_ref_0.xlsx and the rubric's over_edit_avoidance penalty
  - Change: Grader guidance: added a task note that correct fixes of other genuine formula slips (helper column AA, helper rows that skip a row) are within the instruction and do not cost correctness or over_edit_avoidance.
- other finding, major, not in findings.json: Reference answer retains incorrect formulas feeding nine charts
  - Change: Same grader guidance note: correct fixes of the AA helper column are not penalised.

## Confirmed findings not fixed

- [F3](../findings.json): Reference answer changes an input value without supporting data
  - Reason: duplicate-of:F1
