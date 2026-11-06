# Changes: FINCH task-058

Fix summary (from the fix record):

Guidance now accepts both readings of the BY AREA/TRADER total, whose source monthly formulas leave out the Lavorato row.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Trader-block quarterly totals in the answer key use an inconsistent formula range, so an equally valid answer can be marked wrong
  - Change: Grader guidance: one task note added before the output instruction accepting either reading for the 'BY AREA/TRADER' TOTAL CANADA quarterly/full-year totals (with or without the Lavorato row that the source monthly totals leave out). Reference workbook unchanged.
- other finding, major, not in findings.json: Area/trader totals omit the first trader's Q1 income on both input tabs
  - Change: Same guidance task note as another finding (not listed).
