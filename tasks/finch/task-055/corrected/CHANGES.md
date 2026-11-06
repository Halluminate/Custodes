# Changes: FINCH task-055

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: graderGuidance: task-specific note that correl_graph is new, a chart sheet (as in the reference) or worksheet both pass, and the line chart must plot correlation!A3:C138 against H3:H138. Not re-graded locally (no AI-grader stand-in run here).
- other finding, major, not in findings.json: A red-team agent scored 55% of the reward without doing the real work (AI-grader stand-in)
  - Change: graderGuidance: same note, a chart with invented or partial data fails.
