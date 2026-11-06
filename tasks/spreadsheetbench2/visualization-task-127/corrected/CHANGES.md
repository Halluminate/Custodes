# Changes: SpreadsheetBench 2 visualization-task-127

Fix summary (from the fix record):

Widened the golden's print area so its chart renders whole, and told the agent to keep its chart inside the sheet's print area.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_Task 127_golden.xlsx

## Fixed

- [F3](../findings.json) (Reward): SpreadsheetBench 2 official chart checklist: verify_spreadsheetbench2_chart_checklist fails to clear Print_Area when rendering sheets to PDF, completely clipping charts placed outside B2:I47 and causing a false 0/33 verdict on unit 3
  - Change: prompt.md: added "Place the chart on the Target and Ratings sheet and set that sheet's print area so it covers both the chart and the table." so an agent's chart is not clipped by the input print area B2:I47, which the verifier keeps when it exports the sheet (widening the input print area instead shrinks the chart to unreadable size, tested).
- [F2](../findings.json) (Reward): Rendered the way the grader renders it, the GT chart is cut off at Nov-2024, so the ground truth fails its own checklist
  - Change: gt_Task 127_golden.xlsx: widened the Target and Ratings print area from $B$2:$I$76 to $A$1:$P$76 (workbook.xml defined name only) so the golden chart (anchored A4:L37) renders whole; re-rendered with the verifier's _chart_only_copy + LibreOffice: full x-axis to Nov-2025, right Price axis and full legend visible.
- [F1](../findings.json) (Reward): Chart grading can omit charts outside the seed workbook's print area
  - Change: prompt.md: added "Place the chart on the Target and Ratings sheet and set that sheet's print area so it covers both the chart and the table." so an agent's chart is not clipped by the input print area B2:I47, which the verifier keeps when it exports the sheet (widening the input print area instead shrinks the chart to unreadable size, tested).
- other finding, major, not in findings.json: Three checklist items contradict the source data, so a correct chart fails them
  - Change: verifications[0].parameters.checklist and graderGuidance list (ids, name, function, weight, 33 items and >0.7 threshold unchanged): item 15 now 'approximately 26', item 17 'approximately 13', item 24 'approximately 5% (from about 32% to 36% when Sell is at the bottom, about 64% to 68% when Buy is at the bottom)', matching input rows 11 and 30.
- other finding, major, not in findings.json: Three numerical checklist requirements contradict the supplied data
  - Change: Same checklist corrections as another finding (not listed) (items 15, 17, 24).
- other finding, major, not in findings.json: Checklist items contain inaccurate data values/bounds and the golden workbook has broken print area and stacked-line settings
  - Change: Checklist items 15, 17, 24 corrected as in another finding (not listed), and the golden's line overlay changed from stacked to standard (see another finding (not listed)).
- other finding, major, not in findings.json: Ground-truth chart plots its two price lines as a stacked line chart, so the 'Price' line shows Target + Price
  - Change: gt_Task 127_golden.xlsx (on top of the critical-pass print-area fix): xl/charts/chart763.xml <c:lineChart><c:grouping val="stacked"/> -> val="standard"; nothing else changed. LibreOffice render checked: Price now plots below/near Target Price, right axis 0-800. The checklist verifier grades only output.xlsx, so scores are unaffected.
- other finding, major, not in findings.json: Checklist enforces undisclosed series stacking order, segment/line colors, and title/legend labels not stated in task instructions
  - Change: verifications[0].parameters.checklist and graderGuidance list (ids, name, function, weight, 33 items and >0.7 threshold unchanged): item 14 now accepts either stacking orientation as long as it is consistent; items 20-26 give the segment size with positions for both orientations; '(yellow)', '(orange)', '(red)', '(black)' removed from items 21, 22, 25, 26, 30, 31.
- other finding, major, not in findings.json: Grading imposes undisclosed stacking and color conventions
  - Change: Same checklist rewrite as another finding (not listed).
- other finding, major, not in findings.json: Checklist grades colors, stacking order, title and axis range that the instruction never asks for
  - Change: Checklist rewrite as another finding (not listed) (order and colors), plus item 2 now 'The chart has a title that identifies it as the AppLovin analyst target price chart (e.g. ...)' and item 33 now 'The right Y-axis covers the full range of the price lines (from 0 to at least about 740)'.
- other finding, minor, not in findings.json: Instruction names the series 'Average Target Price' but the checklist requires the legend entry 'Target Price'
  - Change: Checklist item 11 now accepts 'Target Price' or 'Average Target Price'.
