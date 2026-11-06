# Changes: FINCH task-059

Fix summary (from the fix record):

FINCH 59: the reference adds an unrequested empty SELLS header block and leaves #DIV/0! in the zero-average row 59. A grader-guidance task note now says the SELLS block is neither required nor an over-edit and accepts any guarded result in row 59.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Ground truth contains an unrequested 'SELLS' table (columns K:O) on TOTAL PHYSICAL GAS that is not in the task instructions or source template
  - Change: grader_guidance.md: added after the opening paragraph: Task note: on TOTAL PHYSICAL GAS, the reference's empty SELLS header block in K6:O9 is not asked for by the instruction, so neither require it nor count it as an over-edit.
- other finding, major, not in findings.json: The prompt asks for one % change column, but the answer key adds two plus an empty SELLS block
  - Change: Same task note as another finding (not listed) (the SELLS block is neither required nor an over-edit).
- other finding, minor, not in findings.json: The answer key's empty SELLS block looks unfinished
  - Change: Same task note as another finding (not listed): the empty SELLS block is no longer required or penalized.
- other finding, minor, not in findings.json: Division-by-zero in Row 59 (Prior Energy Corporation) on TOTAL PHYSICAL GAS is not specified, where GT leaves raw #DIV/0! errors
  - Change: grader_guidance.md: added after the SELLS note: For row 59 (Prior Energy Corporation), whose 30-day average is 0, accept #DIV/0!, 0, blank or any error-guarded result in the two % change cells.
- other finding, minor, not in findings.json: The answer key has #DIV/0! in both new % change cells for the last row
  - Change: Same row-59 sentence as another finding (not listed).
- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: Same task note (another finding (not listed), another finding (not listed)): the unrequested SELLS block and the reference's #DIV/0! cells are the likely cause of the 0.00 grade of the GT. Not re-probed locally.
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Same task note as exploit-probe-0.
