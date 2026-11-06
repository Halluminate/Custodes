# Changes: SpreadsheetBench 2 visualization-task-129

Fix summary (from the fix record):

The six data-label checklist items demanded bare numbers ('20.9', '44.4') while the key chart, the source cells and the $-denominated axis all show currency labels ('$20.90', '$44.40'); those items now say currency formatting is equivalent.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, minor, not in findings.json: Checklist requires bare-number label text ('20.9', '44.4'), but the ground truth and the source data show currency-formatted labels ('$20.90', '$44.40')
  - Change: verify_spreadsheetbench2_chart_checklist parameter 'checklist': the six 'The data labels on the ... bar read ...' items now end with "(currency formatting such as '$20.90' is equivalent)"; the same text is in the guidance list. Ids, names, function and weight unchanged; no other item changed.
