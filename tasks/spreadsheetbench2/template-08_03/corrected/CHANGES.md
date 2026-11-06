# Changes: SpreadsheetBench 2 template-08_03

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, major, not in findings.json: Undisclosed negative sign convention for Dividends Paid and Dividend Per Share
  - Change: Prompt: added one sentence after the Instruction line: 'Show Dividends Paid and Dividend Per Share as negative figures, in line with the sign footnote in the sheet.' This states the key's convention (C26:F27 negative) without changing grading.
- other finding, major, not in findings.json: The answer key expects negative Dividends Paid and a negative Dividend Per Share, and the all-or-nothing grader rejects the usual positive per-share figure
  - Change: Same prompt sentence as another finding (not listed).
