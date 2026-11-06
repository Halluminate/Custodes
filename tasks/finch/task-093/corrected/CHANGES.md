# Changes: FINCH task-093

Fix summary (from the fix record):

Prompt now states the Peak 6x16 convention the key uses (NERC holidays excluded), and a grader note says post-2002 Peak Hours/Value cells, where no Peak deal is active, are not graded against the key's 24-hour fill.

Changed files (in this folder):

- prompt.md
- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Peak 6x16 hours in the answer key use an undisclosed US NERC holiday calendar that the inputs never mention
  - Change: problemStatement: one sentence added after 'For each deal, calculate the corresponding monthly MWh.': 'Peak hours are 16 per day, Monday to Saturday, excluding NERC holidays.' This is the convention of the key's hardcoded Peak!B12:M12 (416, 384, ... 400).
- other finding, minor, not in findings.json: Answer key computes Peak hours for 2003+ as 24 × days, which is wrong for a 6x16 product
  - Change: graderGuidance: task-specific note added before the 'insufficient information' paragraph: "Task-specific note: every Peak deal ends by 31-Dec-2002, so the Peak Hours and Value cells from January 2003 onward carry no MWh. The reference's 24-hours-per-day Peak Hours from 2003 and its Value row stopping at December 2002 are not requirements: any consistent Peak Hours count and a Value row that stops at 2002 or continues are equally correct there."
