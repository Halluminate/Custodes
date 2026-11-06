# Changes: FINCH task-087

Fix summary (from the fix record):

The prompt defines Daily Trading Intensity as the Average Daily Trading Value, but the reference divided it by the number of listed companies in all 25 rows. I set Sheet2_KPIs!E2:E26 in the reference to the RawData average daily trading value. The no-internet finding is an environment issue.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_87_ref_0.xlsx

## Fixed

- [F2](../findings.json) (Verification): Ground truth Sheet2_KPIs 'Daily Trading Intensity' divides Average Daily Trading Value by Total Number of Listed Companies, contradicting the prompt formula
  - Change: gt_87_ref_0.xlsx, Sheet2_KPIs!E2:E26 (Daily Trading Intensity): each value replaced with the same exchange-month's RawData Average Daily Trading Value rounded to 2 decimals, as the prompt defines (e.g. NASDAQ January 2025 37.55 -> 123581.00). No other cell changed.
- [F1](../findings.json) (Verification): GT 'Daily Trading Intensity' does not follow the formula the prompt states (it divides by company count)
  - Change: gt_87_ref_0.xlsx, Sheet2_KPIs!E2:E26 (Daily Trading Intensity): each value replaced with the same exchange-month's RawData Average Daily Trading Value rounded to 2 decimals, as the prompt defines (e.g. NASDAQ January 2025 37.55 -> 123581.00). No other cell changed.
- [F3](../findings.json) (Verification): Reference workbook calculates Daily Trading Intensity contrary to the task
  - Change: gt_87_ref_0.xlsx, Sheet2_KPIs!E2:E26 (Daily Trading Intensity): each value replaced with the same exchange-month's RawData Average Daily Trading Value rounded to 2 decimals, as the prompt defines (e.g. NASDAQ January 2025 37.55 -> 123581.00). No other cell changed.
- other finding, major, not in findings.json: Std Dev definition (sample vs population) is not stated; GT uses sample std dev and a binary grader would reject population std dev
  - Change: graderGuidance: added one line accepting sample or population standard deviation in Sheet5_Summary when the CV uses the same Std Dev (key uses STDEV.S; NYSE 475,575.82 vs STDEV.P 425,367.95).
- other finding, major, not in findings.json: Unstated sample vs. population standard deviation convention and worksheet tab ordering in Sheet5_Summary
  - Change: Same graderGuidance line for the std-dev convention. The tab-order part is not a defect.
- other finding, major, not in findings.json: GT Average Daily Trading Value implies trading-day counts that look wrong for some markets/months
  - Change: graderGuidance: added one line accepting either a published ADTV figure or Total Trading Value / actual trading days (the key's implied day counts are 21 for US January and 20 for Shanghai/Shenzhen May, against 20 and 19 actual).
