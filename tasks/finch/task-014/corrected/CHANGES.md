# Changes: FINCH task-014

Fix summary (from the fix record):

The prompt's 'AA(2) municipal investment bond' matched two curves because the chengtou curve is mistranslated as 'Investment Grade'; the prompt now names the curve the key uses. The key's unrequested translation of D2 is reverted.

Changed files (in this folder):

- prompt.md
- reference/gt_14_ref_0.xlsx

## Fixed

- other finding, major, not in findings.json: 'Municipal investment bond' points to two curves, and the grader accepts only one
  - Change: Prompt: first sentence "Suppose we need to hold a 0.5-year AA(2) municipal investment bond." -> "Suppose we need to hold a 0.5-year AA(2) municipal investment bond, which the model carries as China Investment Grade Bond Yield Curve(AA(2))." This names the curve that the workbook's mistranslated label hides (the key's A3), removing the clash with the callable LGFV curve. Answer key unchanged for this finding.
- other finding, major, not in findings.json: Ambiguous yield curve terminology ('AA(2) municipal investment bond') conflicts with ground truth curve selection
  - Change: Same prompt sentence change as another finding (not listed).
- other finding, major, not in findings.json: Municipal bond curve is ambiguously labeled relative to the reference
  - Change: Same prompt sentence change as another finding (not listed).
- other finding, minor, not in findings.json: Leftover Chinese label in the source, and the GT changes it without being asked
  - Change: gt_14_ref_0.xlsx: 'Holding Period Return Analysis'!D2 'Auxiliary_Column' -> '辅助列' (as in the source), by editing shared string 3 (used only by D2) at XML level. Every other cell is unchanged; the GT still differs from the source only in E1, F1, A3, A13, A16.
- other finding, minor, not in findings.json: Ground truth contains an unrequested translation edit in cell D2 ('辅助列' -> 'Auxiliary_Column') while grader guidance penalizes extra or missing modifications
  - Change: Same GT D2 revert as another finding (not listed).
