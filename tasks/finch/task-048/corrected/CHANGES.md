# Changes: FINCH task-048

Fix summary (from the fix record):

Grader guidance now also accepts value-neutral cleanup of the duplicate extra-depreciation line on the Income Statement.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: GT leaves a duplicate, empty 'extra depreciation' line, so a reasonable cleanup can be marked as over-editing
  - Change: graderGuidance (and agentic grader copy): added after the opening paragraph: "Task note: on the Income Statement, rows 20-21 (Amortization of extra depreciation due to fair market valuation (1)) and row 23 (Amortization of extra depreciation) describe the same item. The reference moves the -140 goodwill amortization from I20 to I18 and repoints I47 to I18, leaving the -9 in row 23. Also accept an output that, in addition, puts the -9 on row 20 instead of row 23 or clears the empty duplicate label, as long as income before income taxes, net income and the cash-flow add-back in I47 keep the reference values."
