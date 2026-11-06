# Changes: FINCH task-080

Fix summary (from the fix record):

Grader note: the reference's made-up arithmetic in input cells and its I1 'Other' rename are not required; the answer is judged on the restored rollup formulas.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Ground truth contains 61 undisclosed literal-number formulas (including 9 multi-term arithmetic expressions) in line-item input cells that cannot be derived from the source workbook or prompt
  - Change: graderGuidance task note: the reference's literal-number formulas in line-item input cells (D8 =139.1-9.8 etc.) are not required; plain-number inputs with the same values are correct.
- other finding, major, not in findings.json: The GT turns input constants into made-up arithmetic that no agent could recover
  - Change: Same task note as another finding (not listed).
- other finding, minor, not in findings.json: Column header cell I1 differs between input workbook ('ETS') and ground truth ('Other') with no instruction to rename the header
  - Change: Same task note: I1 left as 'ETS' or changed to 'Other' are both correct.
- other finding, minor, not in findings.json: The ground truth renames a header cell, which the task never asks for
  - Change: Same I1 task note as another finding (not listed).
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: The GT fails its own judge (0.03/0.03/0.00) because it carries unrequested, unrecoverable edits (I1 rename, literal arithmetic in inputs); the task note above tells the judge these are not required. Not re-graded locally.
