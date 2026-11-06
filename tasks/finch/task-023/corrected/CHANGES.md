# Changes: FINCH task-023

Fix summary (from the fix record):

The only true finding is the excel_add_sheet tool silently dropping pivot, pivot-cache and calcChain parts on save. That is tool behaviour, not a task defect, so no task change is made.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: graderGuidance: added one sentence after the opening paragraph saying the reference's move of rows 88 and 95 to rows 94 and 101 is not part of the task and is not an over-edit either way. This is the likely cause of the low GT grades; not re-graded locally.
- other finding, minor, not in findings.json: The ground truth deletes and moves original source content, breaking the task's own 'preserve all original contents' rule
  - Change: graderGuidance: one added sentence telling the judge the reference's move of rows 88 and 95 is not part of the task, so outputs that keep those rows in place (or move them the same way) are not over-edits or layout errors. GT file unchanged.
