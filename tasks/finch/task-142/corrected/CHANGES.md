# Changes: FINCH task-142

Fix summary (from the fix record):

Corrected three hardcoded answer-key cells on 'Summary Chart ' so PG&E and Station 2 follow the same method as the other 17 points and the grand total equals the sum of the rows. Full pass: The P&L method is unstated and the key adds an out-of-scope totals row. A guidance note accepts either P&L method and says that row is not required.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_142_ref_0.xlsx

## Fixed

- [F4](../findings.json) (Verification): Answer key gives PG&E a P&L of 0 even though it has a nonzero position and a stdev
  - Change: gt_142_ref_0.xlsx 'Summary Chart '!D43 (PG&E P&L) 0 -> -259097.186832 (Office Pos Summary AL8:AL9 x Stdev Table AH8:AH9 x 10,000, +2 stdev).
- [F3](../findings.json) (Verification): Answer key's Station 2 P&L is half the value its own method gives
  - Change: gt_142_ref_0.xlsx 'Summary Chart '!D44 (Station 2 P&L) 33189 -> 66378 (sumproduct AO8:AO18 x AJ8:AJ18 x 10,000 x 0.5, +1 stdev).
- [F1](../findings.json) (Verification): Answer key's Scenario 1 grand-total P&L does not equal the sum of the per-point P&L rows
  - Change: gt_142_ref_0.xlsx 'Summary Chart '!D46 (Sum) -48203351.395266816 -> -50992643.060617216, the sum of the corrected D27:D45.
- [F2](../findings.json) (Verification): Reference grand total does not equal its component P&Ls
  - Change: Same D46 correction (grand total now equals D27:D45).
- [F5](../findings.json) (Verification): Reference P&Ls for PG&E and Station 2 contradict the scenario inputs
  - Change: Same D43 and D44 corrections.
- other finding, critical, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: Unstable guidance grades were driven by the inconsistent answer key; fixed by the D43, D44 and D46 corrections (rerun to confirm).
- other finding, critical, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Low GT grade was driven by the same answer-key errors; fixed by the D43, D44 and D46 corrections (rerun to confirm).
- other finding, major, not in findings.json: P&L method, contract size and stdev scaling are unstated, and the answer key's method differs from the layout the template implies
  - Change: grader guidance: added the task note 'Task note: the workbook does not say whether a point's P&L is the month-by-month sum of position times stdev (as in the reference) or the total position times the average stdev, so accept either method applied consistently, with Scenario 1's stdev multiples (the Stdev Table values are 2 stdev), a 10,000 MMBtu contract and a grand total equal to the sum of the points. The reference's totals row 7 on Office Pos Summary is outside the instruction and is not required.' Not re-graded locally (LLM grader).
- other finding, minor, not in findings.json: Answer key adds out-of-scope totals to Office Pos Summary, including error cells and a hardcoded value
  - Change: Same task note: its last sentence says the reference totals row 7 is not required.
