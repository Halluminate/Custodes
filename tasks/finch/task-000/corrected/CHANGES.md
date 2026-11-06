# Changes: FINCH task-000

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Income Statement totals omit 333 of tenant-services expense
  - Change: grader guidance: added the task note after the opening paragraph: 'Task note: in the source Income Statement the TOTAL column is 333 short because K39 ('Tenant services - other') is a hardcoded 0 while H39 is 333. The reference reconciles each program column and sums those in the total column (total difference 0). Also accept a roll-forward whose total column uses the existing TOTAL-column line items and therefore shows a 333 difference; do not count either choice as a calculation error.'
