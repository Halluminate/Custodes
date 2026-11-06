# Changes: FINCH task-130

Fix summary (from the fix record):

Prompt says 'each unit's amounts' (the key includes vacant and remodeling units), and the grader treats 0 and blank as equal in the frequency columns, since the key shows 0 where the prompt says blank.

Changed files (in this folder):

- prompt.md
- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Prompt says amounts are for each tenant, but the answer key also counts vacant and remodeling units
  - Change: problemStatement, one word in one sentence: "populate each tenant's amounts by week" -> "populate each unit's amounts by week", matching the key, which includes the vacant and remodeling units at their listed rent.
- other finding, major, not in findings.json: Prompt asks for blank cells, but the GT fills them with 0
  - Change: graderGuidance: task-specific note added before the 'insufficient information' paragraph: "Task-specific note: the reference fills the frequency columns with IF formulas that show 0 where a unit has no amount of that frequency (and 0 for the Manager and Maintenance units). For these cells 0 and blank are equivalent, so an output that leaves them blank as the instruction says, or shows 0 like the reference, is correct."
