# Changes: FINCH task-108

Fix summary (from the fix record):

No task change. The only true finding is the excel_write_cell MCP tool rewriting the whole package and dropping comments, calcChain and printer settings. That is a tool bug, not a task defect. Full pass: grader guidance now names the one expected change.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: graderGuidance: added task note after "not the agent's process." stating the single expected change ('2002 Plan'!AJ14 199,060 -> 195,323 from HR!H29), its dependent totals, and what to accept or fail.
- other finding, major, not in findings.json: The grader guidance is generic boilerplate with no task-specific checklist
  - Change: graderGuidance: added task note after "not the agent's process." stating the single expected change ('2002 Plan'!AJ14 199,060 -> 195,323 from HR!H29), its dependent totals, and what to accept or fail.
