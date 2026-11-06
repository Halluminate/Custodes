# Changes: SpreadsheetBench 2 visualization-task-1431124

Fix summary (from the fix record):

Full pass: the golden charts now have markers, as the instruction and checklist require. The ungraded drop-down/dynamic tables cannot be checked by the image-only verifier (see notFixed).

Changed files (in this folder):

- reference/gt_Task 1431124_golden.xlsx

## Fixed

- other finding, minor, not in findings.json: Ground-truth charts have no markers, so the answer key fails its own 'line chart with markers' checks
  - Change: files/gt/gt_Task 1431124_golden.xlsx, xl/charts/chart791.xml and chart792.xml only: each series' <c:marker><c:symbol val="none"/></c:marker> -> <c:marker><c:symbol val="circle"/><c:size val="5"/></c:marker>, chart-level <c:marker val="0"/> -> val="1". Every other part byte-identical; openpyxl reads 8 circle-marker series.

## Confirmed findings not fixed

- [F1](../findings.json): Image-only grader shrinks the whole sheet to a 741x264 px image, so the value checks can't be read, even on the ground truth
  - Reason: infra
