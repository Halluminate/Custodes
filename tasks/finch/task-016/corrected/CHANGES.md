# Changes: FINCH task-016

Fix summary (from the fix record):

Grader-guidance note: facts in the reference that the inputs cannot supply are not required. The output is judged on covering and correctly stating the spreadsheet data in the report's format.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- [F1](../findings.json) (Verification): Much of the ground-truth continuation can't be derived from the inputs, and grading is a binary 'logically equivalent' check
  - Change: Added a grader-guidance note: the reference narrative's outside facts (examples listed) are not required. Completeness means covering every sheet's series in the report's format. Correctness is checked against the spreadsheet data and against the reference where they overlap. Figures that match the reference are allowed, so the reference itself passes.
- other finding, critical, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Added a grader-guidance note: the reference narrative's outside facts (examples listed) are not required. Completeness means covering every sheet's series in the report's format. Correctness is checked against the spreadsheet data and against the reference where they overlap. Figures that match the reference are allowed, so the reference itself passes. The reference failing its own 'logically equivalent' check most likely comes from this underivable content and the over-edit rule. The note lets reference figures stand.
