# Changes: FINCH task-036

Fix summary (from the fix record):

The payables formula did not say which month's volume and price go in each term, nor how to treat the first month; the prompt now states both as the key computes them.

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, major, not in findings.json: Ambiguous '55 days payables' formula in problem statement does not specify whether the two Volume × Price terms refer to the prior month or current month, nor how to handle the first month
  - Change: problemStatement: the formula sentence now reads '(prior month’s day count × prior month’s Volume × prior month’s Price) + (25 × current month’s Volume × current month’s Price)', which is what the key does (Exposure!C7 =$A6*Volumes!B4*Curves!G5+25*Volumes!B5*Curves!G6). Nothing else in that sentence changed.
- other finding, major, not in findings.json: The statement does not say how to handle the first month, which has no prior month
  - Change: problemStatement: one sentence added after the formula: 'For the first month, which has no prior month, use only the 25-day term.' This is the key's row 6 (C6 =25*Volumes!B4*Curves!G5).
