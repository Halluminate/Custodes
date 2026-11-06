# Changes: SpreadsheetBench 2 visualization-task-132

Fix summary (from the fix record):

Dropped the one checklist item that cannot pass on a chart following the required EBIT axis.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: The required EBIT Y-axis maximum ($90m) is below the Mgmt-High data ($100m), so the graded $100m point cannot appear on the chart
  - Change: verifications[0].parameters.checklist: removed item 33 "For chart 'EBIT': The Mgmt-High series data point at FY28E has a value of $100m" (off the required -60..90 axis); 55 items remain, same > 0.7 rule. Ids, name, function, weight unchanged; graderGuidance list renumbered to match.
- other finding, major, not in findings.json: Required EBIT axis clips a point explicitly required by the verifier
  - Change: verifications[0].parameters.checklist: removed item 33 "For chart 'EBIT': The Mgmt-High series data point at FY28E has a value of $100m" (off the required -60..90 axis); 55 items remain, same > 0.7 rule. Ids, name, function, weight unchanged; graderGuidance list renumbered to match.
