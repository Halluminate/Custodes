# Changes: SpreadsheetBench 2 visualization-task-1437004

Fix summary (from the fix record):

Full pass: two checklist items corrected (April Desk drops = 1, garbled August item reworded).

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, minor, not in findings.json: One checklist item has the wrong expected value: April Desk drops should be 1, not 0
  - Change: verifications[0].parameters.checklist item 19 (and graderGuidance list): 'For chart 'Monthly Activity Trends': The Desk drops line shows a value of 0 at April' -> 'For chart 'Monthly Activity Trends': The Desk drops line shows a value of 1 at April' (Sharepoint Tracker row 2, 2025-04-15, Desk Drop TRUE; golden Data!B11 = 1). Ids, name, function, weight, 54 items and threshold unchanged.
- other finding, minor, not in findings.json: April Desk drops checklist value contradicts the source workbook
  - Change: Same checklist item 19 change as another finding (not listed).
- other finding, minor, not in findings.json: One checklist item is garbled: 'The August bar shows the Newsletters no segment'
  - Change: verifications[0].parameters.checklist item 46 (and graderGuidance list): 'For chart 'Share of Activity Per Month': The August bar shows the Newsletters no segment' -> 'For chart 'Share of Activity Per Month': The August bar shows no Newsletters segment' (August Newsletters = 0 in the golden Data!C15), same phrasing as item 41.
