# Changes: FINCH task-066

Fix summary (from the fix record):

The only true finding is about the harness's Excel MCP write tools stripping comments and VML drawings when they save. The task files do not cause it, so nothing in the task changes. Full pass: grader guidance now names the target cell and accepts answers with or without the NET schedule.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The prompt says to fill a single cell, but the answer key fills about 300 cells on a supporting sheet
  - Change: graderGuidance: added task note naming H35 as the target (373,725.36, H33 principal, /365 like the GROSS sheet) and accepting H35 with or without the supporting NET schedule.
