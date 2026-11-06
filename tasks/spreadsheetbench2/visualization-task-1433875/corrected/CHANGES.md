# Changes: SpreadsheetBench 2 visualization-task-1433875

Fix summary (from the fix record):

Checklist item 2 no longer demands an exact title the instruction never gives; it now asks for a title that identifies monthly orders. The Total-in-table-but-not-plotted render dependence is a LibreOffice rendering issue.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, minor, not in findings.json: Verifier checklist requires exact chart title 'Monthly Orders (January-December)' not specified in task instructions
  - Change: verifications[0].parameters.checklist item 2: "The chart title reads 'Monthly Orders (January-December)'" -> "The chart has a title that identifies the data as monthly orders (e.g. 'Monthly Orders')" (the instruction never states a title; the golden's own title differs in spacing and dash); graderGuidance list item 2 updated to match. id, name, function, weight unchanged.
- other finding, minor, not in findings.json: The checklist requires an exact chart title that the instruction never states
  - Change: verifications[0].parameters.checklist item 2: "The chart title reads 'Monthly Orders (January-December)'" -> "The chart has a title that identifies the data as monthly orders (e.g. 'Monthly Orders')" (the instruction never states a title; the golden's own title differs in spacing and dash); graderGuidance list item 2 updated to match. id, name, function, weight unchanged.
- other finding, minor, not in findings.json: Verifier requires an exact chart title absent from the task
  - Change: verifications[0].parameters.checklist item 2: "The chart title reads 'Monthly Orders (January-December)'" -> "The chart has a title that identifies the data as monthly orders (e.g. 'Monthly Orders')" (the instruction never states a title; the golden's own title differs in spacing and dash); graderGuidance list item 2 updated to match. id, name, function, weight unchanged.
