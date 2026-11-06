# Changes: FINCH task-062

Fix summary (from the fix record):

Grader guidance accepts either treatment of the EDF Man analysis block's Line of Credit Balance (F52).

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Unclear whether the EDF Man 'Line of Credit Balance' (F52) counts as a related figure, and the answer key leaves it at 25,000,000
  - Change: Grader guidance: added after the first paragraph: "For this task, the 'EDF Man Line of Credit Analysis' block (sheet 1101, F52 'Line of Credit Balance', 25,000,000 in the reference) may be left as is or set to 0 to match the cleared EDF line; treat either as correct and not as an over-edit." The prompt's 'recalculate any related figures' can fairly cover F52, which the reference leaves at 25,000,000.
