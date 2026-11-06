# Changes: SpreadsheetBench 2 template-14_09

Fix summary (from the fix record):

Only harness/tool findings (missing Python packages, or an MCP save that drops workbook parts). Nothing in the task causes them, so there is no task change. Full pass: prompt now asks to complete the model and states the Year 1 base, the loss-to-lease input and the sign convention the key uses.

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, major, not in findings.json: The one-line instruction hides the real task: rebuilding the whole projection table, and the conventions the grader requires are never stated
  - Change: Prompt: added 'Complete the financial model based on the provided assumptions.' before the concessions instruction (the series' standard instruction; the key fills the whole D32:I46 projection).
- other finding, major, not in findings.json: Grader requires an entire revenue model beyond the stated concessions edit
  - Change: Same prompt sentence as another finding (not listed): the instruction now asks for the whole model the grader checks.
- other finding, major, not in findings.json: Undisclosed convention on whether 'Current Market Rent (Annual)' in C7 is Year 0 (grown in Year 1) or Year 1 (ungrown in Year 1)
  - Change: Prompt: added 'Year 1 uses the current market rent and the Year 1 other income inputs without growth, and loss-to-lease is the stated percentage of market rent in every year.' (key: D32 =C7, D38:D41 =C17/C19/C21/C23, row 33 =-rent*$C$12). Answer key unchanged.
- other finding, major, not in findings.json: Year 1 loss-to-lease has two conflicting inputs, and the ground truth silently picks one
  - Change: Same sentence as another finding (not listed): loss-to-lease is the stated percentage of market rent in every year, so C8 is not the Year 1 figure.
- other finding, major, not in findings.json: Year 1 base and sign convention are not stated but must match the key exactly
  - Change: Year 1 base covered by the another finding (not listed) sentence; prompt also gets 'Show loss-to-lease, concessions and vacancy as negative values.' (key rows 33, 34, 45 are negative and summed).
