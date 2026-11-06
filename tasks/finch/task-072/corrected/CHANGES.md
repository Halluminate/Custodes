# Changes: FINCH task-072

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Source PDF and JPEG only display rounded numbers while ground-truth workbook stores unrounded floats, causing formula outputs in AR4:AS63 to diverge while grader guidance forbids rounding tolerance outside web-search tasks
  - Change: Grader guidance: added a task note that values transcribed as displayed, and formulas computed from them, are equivalent when they differ only by display rounding.
- other finding, major, not in findings.json: Ambiguity as to which derived columns require formulas ('complete any missing formulas') and resulting 1 MW rounding discrepancies in Monthly volume (AI4:AI63) and Contract volumes (D7:H7, AD4:AH63)
  - Change: Same note: derived columns may hold values or formulas, and display-rounding differences are accepted.
- other finding, minor, not in findings.json: Prompt refers to 'the chart' (singular) and source PDF/JPEG clip multiple row and column headers that are unclipped in gt_72_ref_0.xlsx
  - Change: Same note: cut-off labels may be given as shown or in full.
