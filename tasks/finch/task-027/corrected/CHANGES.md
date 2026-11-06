# Changes: FINCH task-027

Fix summary (from the fix record):

The answer key counted open positions as headcount (the Calgary vacancy in HR and the HR vacancy on Canada Support, whose label excludes HR) and put '-' where the prompt says to leave the cell blank. The key now has HR 11, Canada Support 32, blanks for Transaction Support and SAP, and a total of 800.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_27_ref_0.xlsx

## Fixed

- [F1](../findings.json) (Verification): Reference headcounts include vacancies and contradict the required blank-cell convention
  - Change: gt_27_ref_0.xlsx Master: K61 12 -> 11, K67 33 -> 32, K64 and K66 '-' -> blank, K68 (=SUM(K1:K67)) cached 802 -> 800; nothing else changed. grader_guidance.md: one added sentence saying Vacancy rows are not headcount and departments with no data are blank rather than '-'.
