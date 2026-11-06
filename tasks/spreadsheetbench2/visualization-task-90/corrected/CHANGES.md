# Changes: SpreadsheetBench 2 visualization-task-90

Changed files (in this folder):

- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Most of the checklist grades data labels and exact values the instruction never asks for
  - Change: verifications[0].parameters.checklist: removed the 7 "The data label on the <X> bar reads ..." items (21 items remain, including each bar value and cumulative %). Id, name, function, weight unchanged.
