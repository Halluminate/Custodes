# Changes: SpreadsheetBench 2 visualization-task-1411527

Fix summary (from the fix record):

Removed the six checklist items that grade the pre-existing Dollars chart, which the prompt doesn't ask for and which always failed. The openpyxl-missing finding is a sandbox issue.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F2](../findings.json) (Environment & Infra): SpreadsheetBench 2 official chart checklist: verify_spreadsheetbench2_chart_checklist renders the pre-existing Dollars chart as an unreadable 119x81 image and causes false negatives on units 1 and 3
  - Change: Verifier parameters: dropped checklist items 23-28. They grade the pre-existing 'Invoice Dollars Burndown August 2023' chart on the Dollars sheet, which the prompt never mentions, and fit-to-page renders that sheet as a 119x81 speck because of whitespace strings in Dollars!I34 and K36, so the items failed in every trial. The checklist is now the 22 items on the requested Count chart (same threshold, > 0.7), and the same 6 lines are removed from the grader guidance. The finding's other part, the vision judge reading a default-size Count chart at 110 DPI, is a harness rendering matter not addressed here.
- [F1](../findings.json) (Reward): Verifier checklist grades a second pre-existing chart ('Invoice Dollars Burndown August 2023' on the Dollars sheet) not mentioned in the prompt, and the verifier's fit-to-one-page rendering shrinks that sheet's chart to an illegible 119x81 thumbnail due to stray whitespace cells in the input workbook
  - Change: Verifier parameters: dropped checklist items 23-28. They grade the pre-existing 'Invoice Dollars Burndown August 2023' chart on the Dollars sheet, which the prompt never mentions, and fit-to-page renders that sheet as a 119x81 speck because of whitespace strings in Dollars!I34 and K36, so the items failed in every trial. The checklist is now the 22 items on the requested Count chart (same threshold, > 0.7), and the same 6 lines are removed from the grader guidance.
