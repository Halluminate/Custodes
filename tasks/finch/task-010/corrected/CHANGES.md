# Changes: FINCH task-010

Fix summary (from the fix record):

The only true finding is about the excel_read_range tool recalculating OFFSET formulas in LibreOffice and returning Err:502 instead of the stored values. That is tool behaviour, not a task defect, so no task change is made. Full pass: The reference repairs broken external links in the helper sheets and uses yearly Sharpe, trade-count and window conventions that differ from row 23. A guidance note accepts the link repair and either convention.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Broken external workbook references ([2]Timing_Strategy!...) in Benchmark Return and Timing_Strategy_Return cause #VALUE! / #NAME? errors on MDD columns AB, AE, and AG unless the agent fixes unrequested sheets
  - Change: grader guidance: added the task note 'Task note: the hidden helper sheets Benchmark Return and Timing_Strategy_Return link to an external workbook ([2]Timing_Strategy) that is not provided, and the reference repoints them to this workbook's Timing_Strategy sheet. Repairing those links (or computing the yearly maximum drawdowns another valid way) is part of the task and is not an over-edit, and the helper sheets may stay hidden or be shown. The workbook also leaves the yearly conventions open: for the yearly Sharpe ratios (AA, AD) accept annualizing with SQRT(250) as in row 23 or with the square root of the year's trading days as in the reference, for AH accept the year's raw trade count or a count scaled by trading days/250, and accept yearly windows that start at the prior year-end row or at the year's first row. Judge the other cells against the reference.' Not re-graded locally (LLM grader).
- other finding, major, not in findings.json: Drawdown calculation sheets depend on an unstaged external workbook
  - Change: Same task note in the grader guidance.
- other finding, major, not in findings.json: Ambiguous 'established formula logic' between Row 23 (Sample Period) and Ground Truth for Rows 27–39 (Sharpe Ratio and Average Annual Trades)
  - Change: Same task note in the grader guidance.
- other finding, major, not in findings.json: The prompt says to follow the existing approach, but the answer key's yearly Sharpe and Return formulas don't match the aggregated row's formulas
  - Change: Same task note in the grader guidance.
- other finding, minor, not in findings.json: Each yearly window in the answer key includes the prior year's last trading day, so that day is counted in two years
  - Change: Same task note in the grader guidance.
