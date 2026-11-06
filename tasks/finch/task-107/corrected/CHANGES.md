# Changes: FINCH task-107

Fix summary (from the fix record):

The reference workbook does not follow the instruction's layout (left side, section labels, series header), so an instruction-based judge failed the GT itself. One guidance sentence makes the judge accept any non-overwriting, labelled placement and compare the coefficients with the reference.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, critical, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: grader_guidance.md: added after the first paragraph: 'For this task, the reference places the twelve coefficients in Sheet3 G13:H26, to the right of the data and without the section labels or series header the instruction describes, so accept any results table on Sheet3 that does not overwrite existing data, as long as each coefficient sits beside its own lag or lead label, and judge the coefficient values against the reference.' A faithful corrected GT would need the table moved to the left of the data (column inserts and re-pointed formulas), so the grading was fixed instead.
- other finding, major, not in findings.json: The direction of 'shifted 1–6 months later' is ambiguous, and the answer key uses the reverse of the literal reading for lag and lead
  - Change: graderGuidance: appended one sentence to the existing task note accepting the reverse reading of 'shifted 1–6 months later' (lag and lead values swapped) when applied consistently to both sections.
- other finding, major, not in findings.json: Ambiguous series choice and shift conventions for correlation calculations versus ground truth
  - Change: Same guidance sentence as another finding (not listed) (shift-direction part); the levels vs % change part is not a defect (see label).
