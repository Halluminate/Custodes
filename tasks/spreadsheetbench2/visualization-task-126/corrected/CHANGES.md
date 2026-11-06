# Changes: SpreadsheetBench 2 visualization-task-126

Fix summary (from the fix record):

Made the image-only checklist's exact-value items tolerant of axis reading, fixed the golden charts so they render correctly in the verifier (quarter labels, negative columns, title overlap), and removed the seeded print area that hid charts placed outside it. The code-execution policy conflict is infra.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_Task 126_golden.xlsx
- inputs/Task 126_input.xlsx

## Fixed

- [F1](../findings.json) (Reward): Image-only judge has to read ~47 exact data values off charts that have no data labels
  - Change: verifications[0].parameters.checklist: appended ' (approximately, as far as it can be read from the axis scale when no data label is shown)' to the 48 exact-value items (13-54, 56-61); structural items unchanged, 61 items and threshold kept. graderGuidance list updated to match.
- [F3](../findings.json) (Verification): Ground-truth workbook, rendered by the grader's own pipeline, fails its own structural checklist items
  - Change: gt_Task 126_golden.xlsx: chart1 - added the quarter categories (Surprise!$B$51:$B$71, cache copied from the line series) to the two stacked bar series, so the rendered x-axis shows Q3 2020..Q3 2025 instead of 1..21; chart2 - replaced invertIfNegative=1 (LibreOffice draws those columns upward) with invertIfNegative=0 plus per-point orange fills (E46C0A) on the 11 negative quarters, keeping the Excel look, and moved the plot area down (y 0.0545->0.16, h 0.715->0.61) so the title no longer overlaps it. Re-rendered with the verifier's _render_chart_pages: quarter labels, diverging columns and a clear title now show. No cells changed.
- [F2](../findings.json) (Reward): Verifier silently excludes charts outside the seed's print area
  - Change: Removed the Surprise print area (_xlnm.Print_Area Surprise!$B$3:$O$72) from the input workbook (Task 126_input.xlsx) and the golden, so the verifier's LibreOffice render covers the whole sheet and charts placed outside B3:O72 stay visible. Re-rendered the golden: both charts still on the page. No cells changed.
- other finding, minor, not in findings.json: Checklist requires markers on the After Event line, and chart titles look swapped
  - Change: verifications[0].parameters.checklist item 5 and the graderGuidance list: 'The After Event series is displayed as a line with markers' -> 'The After Event series is displayed as a line (markers optional)'. Ids, name, function, weight, 61 items and threshold unchanged.
- other finding, minor, not in findings.json: Ground-truth floating bars use a stacked Base+Differential layout, which breaks for the negative period the checklist grades
  - Change: gt_Task 126_golden.xlsx (on top of the critical-pass golden): Surprise!O67 =D67-E67 -> =ABS(D67-E67) (cached 0.0276) and P67 =E67 -> =MIN(D67,E67) (cached 2.41), XML-level, nothing else changed, so the Q3 2024 floating bar sits between 2.41 and 2.44. Q3 2024 is the only quarter with After Event below Mean. LibreOffice render checked. Not graded (checklist reads output.xlsx only).
