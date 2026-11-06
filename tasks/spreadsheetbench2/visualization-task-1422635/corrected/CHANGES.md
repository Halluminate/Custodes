# Changes: SpreadsheetBench 2 visualization-task-1422635

Fix summary (from the fix record):

The reference chart's Min/Max lines were pale-peach dotted lines. They are now orange and dashed, as the instruction and checklist require. The ungraded helper-formula requirement cannot be added without a new verifier.

Changed files (in this folder):

- reference/gt_Task 1422635_golden.xlsx

## Fixed

- other finding, minor, not in findings.json: The ground truth draws the reference lines dotted and pale peach, while the checklist demands 'dashed' and 'orange'
  - Change: gt_Task 1422635_golden.xlsx, xl/charts/chart781.xml, Min and Max series only: srgbClr f2aa84 -> ed7d31 (orange, 4 occurrences in fill and line) and prstDash sysDot -> dash (2). No other part of the file changed. A LibreOffice render shows orange dashed lines at 7 and 12.
