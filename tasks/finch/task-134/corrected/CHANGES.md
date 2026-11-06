# Changes: FINCH task-134

Fix summary (from the fix record):

Grader guidance gained a task-specific note: the reference's unstated choices (date row also shifted, empty Short Term banner and some spacer rows kept, hidden row 12 unhidden) are accepted either way.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The prompt doesn't say which non-data rows survive "delete all rows that are not marked violation", and the binary score depends on the reference's own choice
  - Change: graderGuidance: task-specific note after the opening paragraph. The required work is the title shift and deleting every non-VIOLATION table row (TOTAL WEST POWER included, as the instruction says); keeping or removing blank spacer rows and the empty WEST POWER SHORT TERM banner is accepted either way.
- other finding, major, not in findings.json: The prompt asks to shift one merged title, but the reference also shifts the merged date row A2:I2
  - Change: Same note: moving only the A1 title or also the A2:I2 date row are both accepted, and neither is an over-edit.
- other finding, major, not in findings.json: The reference unhides a row that was hidden in the source, which the prompt never asks for
  - Change: Same note: source row 12 may stay hidden or be unhidden; the reference's unhiding is not required and keeping it hidden is not a difference.
