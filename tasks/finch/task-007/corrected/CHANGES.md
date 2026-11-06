# Changes: FINCH task-007

Fix summary (from the fix record):

The guidance compared 'output.xlsx' to 'answer.xlsx' with no translation criteria, and the GT graded 0.00/0.88/0.03. A guidance note now states how to judge a .docx translation.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: grader guidance: added the task note 'Task note: this is a Word translation task, so read 'output.xlsx' and 'answer.xlsx' below as the output and reference .docx files, and treat the reference as one valid English translation: pass the output if it translates all of the source's text, tables, figures, footnotes and chart labels accurately and keeps a neat layout, even where its wording differs from the reference.' Not re-graded locally (LLM grader).
- other finding, major, not in findings.json: Grader guidance is a generic spreadsheet template that doesn't fit this Word translation task
  - Change: Same task note in the grader guidance.
