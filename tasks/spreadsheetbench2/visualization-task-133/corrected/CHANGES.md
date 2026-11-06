# Changes: SpreadsheetBench 2 visualization-task-133

Fix summary (from the fix record):

SB2 chart checklist: item 5 reworded to the prompt's Battery Charge Progress (%) label with the title optional, and two colour items added (green-toned filled segment, light grey unfilled segment), matching the golden chart (8ed973 / bfbfbf). Threshold >0.7 unchanged.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: The instruction's colour and helper-table requirements are not in the grading checklist
  - Change: verifications[0].parameters.checklist (+ graderGuidance list): added 'The filled (charged) segment is green-toned' and 'The unfilled (remaining) segment is light grey' (9 -> 11 items, id/name/function/weight and >0.7 threshold unchanged; golden uses 8ed973 green and bfbfbf grey). The helper-table requirement cannot be seen by the image-only verifier and is left to the prompt.
- other finding, major, not in findings.json: The sole grading checklist omits explicit color and helper-table requirements
  - Change: Same two colour items as another finding (not listed).
- other finding, minor, not in findings.json: Checklist item names 'Battery Charge Level', which appears nowhere in the data, and the ground-truth chart shows no label for it
  - Change: Checklist item 5 'The chart represents Battery Charge Level' -> 'The chart represents the Battery Charge Progress (%) value from Sheet1 (a title or label naming it is optional)', so the untitled golden chart can pass it.
