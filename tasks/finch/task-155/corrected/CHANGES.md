# Changes: FINCH task-155

Fix summary (from the fix record):

No task change. The only finding is that the harness's excel_write_range tool drops cell comments and calcChain when it saves. The tool causes this, not the task files. Full pass: two guidance task notes (H26/H27 +0.4 plugs; I24/I26 adjustments and row 26 fill optional).

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Ground truth hardcodes rounded integers with undisclosed +0.4 plugs in HR!H26 and HR!H27 while grader guidance forbids numeric tolerance for non-web-search tasks
  - Change: graderGuidance: task note sentence that the reference +0.4 on HR!H26/H27 are hand-tie plugs and exact or dollar-rounded HR Detail Adj. Total amounts match.
- other finding, major, not in findings.json: Reference answer adds unexplained +0.4 plugs to ENA and ENW, so its total no longer matches HR Detail
  - Change: graderGuidance: task note sentence that the reference +0.4 on HR!H26/H27 are hand-tie plugs and exact or dollar-rounded HR Detail Adj. Total amounts match.
- other finding, major, not in findings.json: Ground truth modifies percentage formulas in HR!I24 and HR!I26 and strips row 26 fill color (HR!A26:J26) without instruction in the prompt
  - Change: graderGuidance: task note sentence that keeping or removing the I24/I26 -0.001/-0.002 adjustments and the row 26 fill are both acceptable.
- other finding, major, not in findings.json: Reference answer also edits the % column (removes plugs in I24 and I26), which the instruction never asks for
  - Change: graderGuidance: task note sentence that keeping or removing the I24/I26 -0.001/-0.002 adjustments and the row 26 fill are both acceptable.
