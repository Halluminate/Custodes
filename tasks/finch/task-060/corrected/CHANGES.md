# Changes: FINCH task-060

Fix summary (from the fix record):

Rebuilt the reference workbook from the actual input file: it now holds an Excel table over the input's All Natural Gas data, filtered on Short Name by red cell fill. The old reference came from a larger, different version of the sheet.

Changed files (in this folder):

- reference/gt_60_ref_0.xlsx

## Fixed

- [F1](../findings.json) (Verification): Ground truth workbook does not contain an Excel Ctrl+T table and appears to have been generated from a different source workbook than 60_src_0.xlsx
  - Change: gt_60_ref_0.xlsx is now 60_src_0.xlsx plus a Ctrl+T table 'Table1' on 'All Natural Gas'!A3:S107 (TableStyleMedium2) with a colorFilter on column 2 (Short Name, under COUNTERPARTY) for red fill (FF0000). Rows 4-101 are hidden, leaving the six red-filled rows 102-107 (FB-CENT1..6-CAD-GD), the same six entries the old reference showed. No extra 'Sitara GCP ID' column and no extra rows. All cell values match the input.
- [F2](../findings.json) (Environment & Infra): The reference workbook is a different, larger version of the sheet than the agent's input file
  - Change: Same rebuild: the reference sheet now has the input's 107 rows and 19 columns.
