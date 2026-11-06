# Changes: FINCH task-078

Fix summary (from the fix record):

The reference no longer edits a sub-sheet or reorders tabs: Other!C1 is back to the source 'ETS' and the tab order is the source's (... GCO_HPL, Other, ETS OPS-EOTT).

Changed files (in this folder):

- reference/gt_78_ref_0.xlsx

## Fixed

- other finding, minor, not in findings.json: GT edits a sub-sheet and reorders tabs, against the instruction to update only the summary
  - Change: files/gt/gt_78_ref_0.xlsx (XML-level): Other!C1 back to the source value 'ETS' (shared string 154, as in the source); tab order restored to the source's (GCO_HPL, Other, ETS OPS-EOTT) by swapping the two <sheet> entries and their print-area/print-title localSheetId values 6/7 and the docProps/app.xml titles. No summary cell or value changed; the reference's ETS summary edits are kept. LibreOffice opens it with the source tab order.
