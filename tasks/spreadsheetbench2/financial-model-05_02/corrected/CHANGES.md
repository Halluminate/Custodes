# Changes: SpreadsheetBench 2 financial-model-05_02

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, major, not in findings.json: Graded scope includes the Pre-op column of Total Expenses, but the instruction limits the ask to Apr-25 to Jun-33
  - Change: Prompt, one sentence changed: "In the IS - Mgmt Co. sheet, compute Total Expenses from Apr-25 to Jun-33." -> "In the IS - Mgmt Co. sheet, compute Total Expenses for the Pre-op column and from Apr-25 to Jun-33."
