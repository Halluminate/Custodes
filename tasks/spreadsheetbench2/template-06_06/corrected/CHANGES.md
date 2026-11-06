# Changes: SpreadsheetBench 2 template-06_06

Fix summary (from the fix record):

The answer key's subtotal and portfolio Y/Y growth rows weighted segment growth by current revenue instead of prior-year revenue, failing correct work at C22. Recomputed those 12 cells as total over implied prior-year revenue minus 1. Full pass: the cell check no longer grades the FY-column growth cells and 1Q26 Q/Q cells that the key leaves blank without any source requiring it.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_06_06_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check fails mathematically correct aggregate Y/Y Growth % at Revenue_Forecast!C22 due to flawed ground truth
  - Change: files/gt/gt_06_06_golden.xlsx 'Revenue_Forecast'!C22:F22, C37:F37, C42:F42 (hardcoded values): replaced the current-revenue-weighted average of segment Y/Y rates with true aggregate Y/Y growth = total revenue / sum(segment revenue/(1+segment Y/Y)) - 1 (e.g. C22 0.144895 -> 0.143332, C37 0.137219 -> 0.136652, C42 0.140743 -> 0.139709). No other cell changed. Local check: patched GT and input+GT edits both PASS
- [F1](../findings.json) (Verification): Golden solution uses mathematically flawed current-revenue-weighted average for subtotal and portfolio Y/Y Growth % instead of prior-year revenue weighting, causing cell C22 to fail under the 1% relative tolerance
  - Change: files/gt/gt_06_06_golden.xlsx 'Revenue_Forecast'!C22:F22, C37:F37, C42:F42 (hardcoded values): replaced the current-revenue-weighted average of segment Y/Y rates with true aggregate Y/Y growth = total revenue / sum(segment revenue/(1+segment Y/Y)) - 1 (e.g. C22 0.144895 -> 0.143332, C37 0.137219 -> 0.136652, C42 0.140743 -> 0.139709). No other cell changed. Local check: patched GT and input+GT edits both PASS
- [F3](../findings.json) (Verification): Answer key gets total-row Y/Y growth wrong: it weights segment Y/Y by current-period revenue, so the correct method fails the pass/fail check
  - Change: files/gt/gt_06_06_golden.xlsx 'Revenue_Forecast'!C22:F22, C37:F37, C42:F42 (hardcoded values): replaced the current-revenue-weighted average of segment Y/Y rates with true aggregate Y/Y growth = total revenue / sum(segment revenue/(1+segment Y/Y)) - 1 (e.g. C22 0.144895 -> 0.143332, C37 0.137219 -> 0.136652, C42 0.140743 -> 0.139709). No other cell changed. Local check: patched GT and input+GT edits both PASS
- other finding, major, not in findings.json: Undisclosed constraint on whether FY2026 Y/Y Growth % cells (G22, G37, G42) should be left blank or populated
  - Change: verifications[0].answer_position: 'Revenue_Forecast'!B2:G42 -> same range minus the growth cells the key leaves blank with no source saying they must stay blank: FY column G Q/Q and Y/Y rows (G9,G10,G13,G14,G17,G18,G21,G22,G28,G29,G32,G33,G36,G37,G41,G42) and 1Q26 Q/Q (C9,C13,C17,C21,C28,C32,C36,C41). graderGuidance range updated to match. Real scorer: patched golden PASS, input+key changes PASS, input+key changes with FY Y/Y in G10/G22 and 'n/a' in C9 PASS (was FAIL reg=0.9838), untouched input FAIL.
- other finding, major, not in findings.json: Graded range covers FY-column growth cells and 1Q26 Q/Q cells that GT leaves blank, while the instructions ask for 'FY totals'
  - Change: Same answer_position change as another finding (not listed).

## Confirmed findings not fixed

- [F2](../findings.json): Incorrect aggregate year-over-year growth in the answer key rejects correct financial calculations
  - Reason: duplicate-of:F3
