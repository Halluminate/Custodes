# Changes: FINCH task-154

Fix summary (from the fix record):

Only harness/tool findings (missing Python packages, or an MCP save that drops workbook parts). Nothing in the task causes them, so there is no task change. Full pass: a guidance task note says the Rate cells are already filled.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, minor, not in findings.json: The task asks the agent to fill in 'Rate', but every Rate cell is already filled in the source
  - Change: grader_guidance.md: added after the opening paragraph: Task note: the Rate cells J12:J15 in FR finances are already filled in the source and stay as they are in the reference, so do not count them as missing work, and accept an output that leaves them unchanged or rewrites them with the same values.
- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: Same task note as another finding (not listed): the prompt lists Rate as missing although the source and reference already hold it, the likely reason one grade failed the GT for not completing Rate. Not re-probed locally.
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Same task note as exploit-probe-0.
