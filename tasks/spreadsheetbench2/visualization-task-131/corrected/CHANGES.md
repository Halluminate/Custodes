# Changes: SpreadsheetBench 2 visualization-task-131

Fix summary (from the fix record):

The 7 checklist items that asked an image-only judge for unrounded values and exact Y-axis positions now ask for the rounded values the required labels show, with approximate positions.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: SpreadsheetBench 2 official chart checklist: verify_spreadsheetbench2_chart_checklist fails all 7 Y-axis coordinate items on every unit and produces a false negative (score=0) on unit 2
  - Change: verifications[0].parameters.checklist items 11, 13, 15, 17, 19, 21, 23 (and the graderGuidance list): exact decimal values and Y-axis start/end points replaced by the rounded values the required 'No decimals' labels show, with the decimals in brackets, plus '(approximate positions, read from the bar heights and data labels when no value axis is shown)', e.g. 17 'The Employee Costs bar value is about -5 (-5.1) and runs from about 19 down to about 14 (...)'. Ids, name, function, weight, 24 items and the >0.7 threshold unchanged.
- other finding, major, not in findings.json: Checklist items 11, 13, 15, 17, 19, 21, and 23 require unrounded decimal values and exact Y-axis start/end coordinates that are not in the prompt, absent from the ground truth's visual rendering, and unverifiable by the image-only judge
  - Change: verifications[0].parameters.checklist items 11, 13, 15, 17, 19, 21, 23 (and the graderGuidance list): exact decimal values and Y-axis start/end points replaced by the rounded values the required 'No decimals' labels show, with the decimals in brackets, plus '(approximate positions, read from the bar heights and data labels when no value axis is shown)', e.g. 17 'The Employee Costs bar value is about -5 (-5.1) and runs from about 19 down to about 14 (...)'. Ids, name, function, weight, 24 items and the >0.7 threshold unchanged.
- other finding, major, not in findings.json: Checklist asks the judge to confirm one-decimal values that the required 'No decimals' labels hide, on a chart with no value axis
  - Change: verifications[0].parameters.checklist items 11, 13, 15, 17, 19, 21, 23 (and the graderGuidance list): exact decimal values and Y-axis start/end points replaced by the rounded values the required 'No decimals' labels show, with the decimals in brackets, plus '(approximate positions, read from the bar heights and data labels when no value axis is shown)', e.g. 17 'The Employee Costs bar value is about -5 (-5.1) and runs from about 19 down to about 14 (...)'. Ids, name, function, weight, 24 items and the >0.7 threshold unchanged.
