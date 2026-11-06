# Changes: SpreadsheetBench 2 visualization-task-1426290

Fix summary (from the fix record):

Full pass: golden chart now has markers on the three lines as the instruction and checklist require. Data-sheet work cannot be graded by the image-only verifier.

Changed files (in this folder):

- reference/gt_Task 1426290_golden.xlsx

## Fixed

- other finding, minor, not in findings.json: Ground-truth chart fails its own 'line with markers' checklist items
  - Change: files/gt/gt_Task 1426290_golden.xlsx, xl/charts/chart787.xml only: the three line series' <c:marker><c:symbol val="none"/></c:marker> -> <c:marker><c:symbol val="circle"/><c:size val="5"/></c:marker>, lineChart <c:marker val="0"/> -> val="1". Every other zip part byte-identical.
