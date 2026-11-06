# Changes: FINCH task-026

Fix summary (from the fix record):

Grader guidance gained a chart-specific note: what each of the six charts must show, optional lines and UDC Resources accepted either way, and the unrequested average-price cells in the key not required.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Ground-truth workbook (gt_26_ref_0.xlsx) contains 12 added formula/label cells (A9, E9, AR1, AS1 across Scenario1–Scenario3) that were stripped from 26_src_0.xlsx but are never requested in the prompt
  - Change: graderGuidance: added a task-specific note that the AR1:AS1 and A9:E9 average-price cells in the reference are not requested and must not be required.
- other finding, major, not in findings.json: Stacked hedge-coverage series: the prompt says contract MW, but the reference also stacks UDC Resources
  - Change: Same note: the stacked chart passes with the contract columns with or without UDC Resources (AB).
- other finding, major, not in findings.json: Optional chart elements and a binary 'equivalent to reference' rubric point the grader in different directions
  - Change: Same note: lists what each chart must show (type, series/ranges, axis units), says the Short and fixed-price lines are optional, and that titles, axis-title wording, colors and placement may differ. Official judge text kept verbatim.
