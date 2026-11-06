# Changes: FINCH task-136

Changed files (in this folder):

- prompt.md
- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: Prompt end date corrected (another finding (not listed)) and a task-specific note added to the grader guidance before "If you feel there is insufficient information": "Task-specific note: the reference has four chart sheets (Producing, East, West, Total), each a line chart of the six seasons 1994/95 to 1999/00 taken from the Data sheet's weekly storage levels for weeks ending 5-Nov through 28-Oct, with a dashed vertical line between WINTER and SUMMER in early April. Judge the output's charts on those elements. Charts placed on worksheets with those names are acceptable, and title wording, legend size, colours and line styles may differ from the reference, which also carries one stray data label that the output need not copy." Not re-graded locally (LLM grader).
- other finding, major, not in findings.json: The prompt says the X-axis runs 5-Nov to 21-Oct, but the reference charts run to 28-Oct
  - Change: Prompt: "(from 5-Nov to 21-Oct)" -> "(from 5-Nov to 28-Oct)", matching the reference charts and the data, which run through row 57.
- other finding, major, not in findings.json: The grader guidance is a generic Excel-comparison template that describes inputs the agentic grader does not receive
  - Change: Same task-specific guidance note as exploit-probe-0 (chart sheets, six seasons, 5-Nov to 28-Oct, dashed WINTER/SUMMER divider in early April, styling differences acceptable).
