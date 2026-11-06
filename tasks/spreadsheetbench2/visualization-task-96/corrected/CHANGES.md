# Changes: SpreadsheetBench 2 visualization-task-96

Fix summary (from the fix record):

Two checklist items required a 'Sales' category under the Sales department, which the data does not have (Sales has only Travel), so no correct chart could satisfy them. Both items are removed from the checklist; the golden file's missing sunburst chart is left as is because the checklist judge does not read it and a faithful chartEx could not be rebuilt and checked here.

Changed files (in this folder):

- grading.json (verifier parameters)

## Fixed

- [F2](../findings.json) (Reward): Checklist requires nonexistent 'Sales' category under Sales department and corrupted golden file lacks a valid chart
  - Change: verifications[0].parameters.checklist: removed "The Sales department contains a category segment labeled 'Sales' in the middle ring" and "The Travel category is larger than the Sales category within the Sales department" (27 items remain; id, name, function, weight unchanged). The other half of this finding (GT has no chart) is covered under F1.

## Confirmed findings not fixed

- [F1](../findings.json): Ground-truth golden file has no chart, only an 'isn't available' placeholder shape
  - Reason: cannot-fix-safely: the GT sunburst is an Excel chartEx part that was lost on resave. Rebuilding it by hand could not be checked without Excel (LibreOffice does not render chartEx), and verify_spreadsheetbench2_chart_checklist grades output.xlsx against the checklist only, so the GT file does not affect scores.
