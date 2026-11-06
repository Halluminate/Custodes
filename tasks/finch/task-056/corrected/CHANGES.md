# Changes: FINCH task-056

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: Same task note: tells the grader the reference's non-zero Jan-Mar Check row comes from the source's Summary range and either form is accepted (not regraded here).
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Same task note as exploit-probe-0.
- other finding, major, not in findings.json: Answer key copies the Summary's Jan–Mar trader-total bug, so its own check row fails by C$-equivalent US$11.8M
  - Change: Grader guidance: task note accepts SUM-USD trader totals that copy the Summary's Jan-Mar range (reference) or include the Lavorato row so the check ties to zero, not counted as an over-edit.
- other finding, major, not in findings.json: Summary's Q1 trader totals omit an entire trader and do not reconcile
  - Change: Same task note on the Lavorato omission.
