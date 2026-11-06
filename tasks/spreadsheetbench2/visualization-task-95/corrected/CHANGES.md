# Changes: SpreadsheetBench 2 visualization-task-95

Fix summary (from the fix record):

No change. The only true finding is that the sandbox's python3 cannot load openpyxl (or run at all) although the shared SpreadsheetBench task context advertises the Python workflow; that is an environment issue, not a task defect. Full pass: five checklist bubble positions corrected to the input data.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: The checklist's 'approximate' bubble positions for several products don't match the input data, so a correct chart can fail items
  - Change: verifications[0].parameters.checklist and graderGuidance: X positions of the five items that disagree with Strategy!N5:N13 set to the data (#14 Product D: 70,000 -> 64,500; #16 Product B: 70,000 -> 75,000; #20 Product A: 105,000 -> 100,000; #22 Product F: 105,000 -> 99,000; #24 Product C: 125,000 -> 120,000). Y values, other items and weights unchanged.
