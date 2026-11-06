# Changes: FINCH task-164

Fix summary (from the fix record):

The judge text compared output.xlsx with answer.xlsx in a PDF translation task and the GT has a typo. A guidance note states how to judge the translation.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Grader guidance is a generic spreadsheet template that refers to output.xlsx and answer.xlsx in a PDF translation task
  - Change: grader guidance: added the task note 'Task note: this is an image-to-PDF translation task, so read 'output.xlsx' and 'answer.xlsx' below as the agent's PDF and the reference gt_164_ref_0.pdf, and treat the reference as one valid Chinese translation of the screenshot (its 投资拔付 is a typo for 投资拨付). Pass the output if it translates every row, figure and footnote of the table accurately into Chinese (simplified or traditional) in a clear table grid, even where its wording or finance terms differ from the reference.' Not re-graded locally (LLM grader).
- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: Same task note in the grader guidance.
- other finding, minor, not in findings.json: Typo in the ground-truth translation: 投资拔付 should be 投资拨付 ('disbursements')
  - Change: Same task note in the grader guidance.
- other finding, minor, not in findings.json: Statement says 'from the English PDF', but the only input is a JPEG, and the Chinese script is not specified
  - Change: Same task note in the grader guidance.
