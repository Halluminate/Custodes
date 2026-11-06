# Changes: FINCH task-035

Fix summary (from the fix record):

The index used for dollar-volume conversion is unstated for Volumetric operators and the reference's Conoco conversion contradicts its sheet. A guidance note accepts 5.81 or 5.82 for each conversion.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Undisclosed index assignment (SJ $P$10 vs AVG $P$11) for the 10 Volumetric operators on the summary sheet
  - Change: grader guidance: added the task note 'Task note: the summary sheet lists three index prices (SJ 5.81 in P10, AVG 5.82 in P11, NTXPH 5.82 in P12), nothing in the workbook says which index converts the Volumetric operators' volumes to dollars, and the reference converts Conoco's dollars to volume (C30) at SJ although the Conoco sheet values its imbalance at AVG. For every dollar-volume conversion on the summary accept either 5.81 or 5.82, with the totals that follow from that choice, and judge the operator balances taken from the operator sheets, the as-of dates and the sign convention against the reference.' Not re-graded locally (LLM grader).
- other finding, major, not in findings.json: Ground truth formula for Conoco volume (summary!C30) uses $P$10 (5.81), contradicting Conoco!C37 which explicitly uses summary!P11 (5.82)
  - Change: Same task note in the grader guidance.
- other finding, major, not in findings.json: Index choice (SJ 5.81 vs AVG 5.82) for converting between dollars and volume is unstated, and the GT applies it inconsistently (including valuing Conoco at a different index than its own sheet uses)
  - Change: Same task note in the grader guidance.
- other finding, major, not in findings.json: Reference uses a different Conoco conversion index than the source
  - Change: Same task note in the grader guidance.
- other finding, major, not in findings.json: Grader guidance is a generic binary equivalence rubric with no task-specific checks or tolerances
  - Change: Same task note in the grader guidance.
