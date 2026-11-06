# Changes: FINCH task-005

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, minor, not in findings.json: A plausible wrong value at gt_5_ref_0.xlsx Summary!O47 still scored 100% of full reward — a verifier is blind to it
  - Change: Grader guidance: task note tells the grader to check every visible figure against the source, including the 'Total All Raptor Structures' row and the footnote amounts.
- other finding, major, not in findings.json: Reference workbook gt_5_ref_0.xlsx stores unrounded floats in 46 cells that are only shown rounded in 5_src_0.pdf and 5_src_1.jpeg, while grader_guidance restricts rounding tolerance to web-search tasks
  - Change: Grader guidance: task note that values transcribed as displayed, and totals/products computed from them, are equivalent to the reference's unrounded values when they differ only by display rounding.
- other finding, minor, not in findings.json: Reference workbook gt_5_ref_0.xlsx contains hidden row 44 (B44=18008400) and out-of-print-area cells not visible in 5_src_0.pdf or 5_src_1.jpeg
  - Change: Grader guidance: task note that the reference's hidden row 44 (B44) and column R are not in the source, so their absence is not an omission.
- other finding, major, not in findings.json: The reference workbook holds more precision and extra content than the visible source
  - Change: Same task note: display-rounding equivalence plus hidden row 44 / column R not counted as omissions.
