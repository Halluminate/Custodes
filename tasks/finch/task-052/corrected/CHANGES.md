# Changes: FINCH task-052

Fix summary (from the fix record):

Grader guidance now tells the judge that the source PDF and reference have no chart, so a missing chart is not a completeness failure.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Task statement requires transcribing a non-existent chart while grader guidance instructs judge to evaluate completeness against the instruction rather than the reference
  - Change: graderGuidance (and agentic grader copy): added after the opening paragraph: "Task note: 52_src_0.pdf holds only the cost table and comments, with no chart, and the reference workbook has no chart either, so the instruction's "(including the chart)" has nothing to transcribe here. Do not fail an output for leaving the chart out, nor for adding a chart that correctly plots the table's own figures."
- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: graderGuidance (and agentic grader copy): added after the opening paragraph: "Task note: 52_src_0.pdf holds only the cost table and comments, with no chart, and the reference workbook has no chart either, so the instruction's "(including the chart)" has nothing to transcribe here. Do not fail an output for leaving the chart out, nor for adding a chart that correctly plots the table's own figures."
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: graderGuidance (and agentic grader copy): added after the opening paragraph: "Task note: 52_src_0.pdf holds only the cost table and comments, with no chart, and the reference workbook has no chart either, so the instruction's "(including the chart)" has nothing to transcribe here. Do not fail an output for leaving the chart out, nor for adding a chart that correctly plots the table's own figures."
