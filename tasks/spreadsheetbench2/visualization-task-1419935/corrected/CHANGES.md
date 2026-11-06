# Changes: SpreadsheetBench 2 visualization-task-1419935

Fix summary (from the fix record):

The chart checklist mixed two denominators for the Player pie (N/A excluded vs included), miscounted slices, and had three items an image-only judge cannot see (two slicers, the sheet tab name). I made the player items accept either denominator and dropped the three unseeable items.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F7](../findings.json) (Reward): SpreadsheetBench 2 official chart checklist: verify_spreadsheetbench2_chart_checklist trivially fails (score 0.0) across all units due to LibreOffice rendering limitations on slicers/sheet tabs and contradictory checklist items
  - Change: verifications[0].parameters.checklist: removed old items 5, 6 (slicers, not rendered by LibreOffice) and 9 (sheet tab name, not in the render); items 8, 19-25 for 'Count of Player Activities' rewritten to accept N/A-excluded or N/A-included shares, 'O' or '0', and no longer contradict each other. 26 items -> 23, threshold unchanged.
- [F5](../findings.json) (Reward): Self-contradictory checklist items and undisclosed 'N/A' filtering for 'Count of Player Activities' and 'Number of Game Events'
  - Change: Old checklist items 19-23 now read e.g. "The 6 slice value is 28% (23% if an 'N/A' slice is kept in the pie)"; item 24 now only requires player 6 to be the largest slice; item 25 lists the 8 players plus an optional N/A slice; item 8 accepts '0' for 'O'.
- [F1](../findings.json) (Reward): The checklist contradicts itself on the Player pie chart, so some items fail whatever the agent builds
  - Change: Same checklist rewrite as F5: no pair of Player-chart items can now contradict each other.
- [F3](../findings.json) (Reward): Slicer items can never pass, and the allowed tools cannot build slicers or native pivot tables
  - Change: Removed the two slicer items (old 5 and 6) from the image-only checklist; the Opp-only filter on the Event chart is still checked through the Opp slice values (new items 9-15 and 23).
- [F4](../findings.json) (Verification): Player-percentage answer key contradicts the fixture and itself
  - Change: Same checklist rewrite as F5 (both 9/32 and 9/39 shares accepted, 8 players + optional N/A).
- [F2](../findings.json) (Reward): Slicer connectivity and selection are checked through an inadequate rendering-only verifier
  - Change: Removed the two slicer items from the rendering-only checklist (see F3).

## Confirmed findings not fixed

- [F6](../findings.json): The ground-truth workbook fails its own checklist
  - Reason: cannot-fix-safely: the GT is a LibreOffice round-trip of the official Excel answer that lost its pivot filters and slicer caches; rebuilding pivot charts with filtered caches and slicers by hand would not be faithful. The chart verifier reads only the agent output, not the GT.
