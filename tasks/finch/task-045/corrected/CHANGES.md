# Changes: FINCH task-045

Fix summary (from the fix record):

The reference commentary cites business drivers that are not in the workbook. A guidance note keeps the headcount figures strict and accepts any data-consistent drivers in the three sections.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Reference commentary in Summary!I6:I30 relies on external business facts absent from the source workbook while grader_guidance requires logical equivalence to the reference text
  - Change: grader guidance: added the task note 'Task note: the workbook holds only headcount and deal figures, so the reference's specific business drivers in Summary!I6:I30 (EOL support staff, the transfer of about 25 people, the commercialization effort, London growth, the Freight Markets Group, the Forest Products and Steel start-up) cannot be derived from it and are not required. Judge the Plan and Actual headcounts in D8:G14 against the reference, and pass the commentary if it has Enron Americas, EGM and EIM sections on the right of the Summary sheet whose drivers are reasonable and consistent with the workbook's headcount and deal data, even where its wording, sub-periods and specific drivers differ from the reference.' Not re-graded locally (LLM grader).
- other finding, major, not in findings.json: The reference commentary depends on business facts that appear in no agent-visible source, so the graded commentary is effectively impossible to match
  - Change: Same task note in the grader guidance.
- other finding, major, not in findings.json: Reference analysis requires business context absent from the task inputs
  - Change: Same task note in the grader guidance.
- other finding, major, not in findings.json: The grader guidance is a generic Excel-equivalence template with no task-specific rubric for the commentary
  - Change: Same task note in the grader guidance.
