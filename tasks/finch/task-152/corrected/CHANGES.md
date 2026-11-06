# Changes: FINCH task-152

Fix summary (from the fix record):

A guidance note accepts both day-weighted and simple period averages and stops the judge from requiring the reference's unrequested helper column and cc-list edit.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Ambiguous definition of 'period average daily quantity' (day-weighted vs. simple monthly average)
  - Change: graderGuidance: task note accepts either the day-weighted period average (5,350,000/214 = 25,000, reference G32) or the simple average of E22:E28 (about 24,931).
- other finding, major, not in findings.json: 'Period average daily quantity' and 'months already included' are ambiguous, the outcome is pass/fail, and the grader guidance gives no tolerance or alternative readings
  - Change: Same period-average task note as another finding (not listed).
- other finding, minor, not in findings.json: Ground truth contains unrequested CC-list edits and a helper column not mentioned in the prompt
  - Change: graderGuidance: task note says the reference's Number of Days column (I14:I30) and the cc-list edit (T. Powell -> D. Avila, moved up a row) are not requested, are not required, and keeping the original cc list must not fail.
- other finding, minor, not in findings.json: Ground truth includes a distribution-list change that the task never asked for (T. Powell replaced by D. Avila, block moved up one row)
  - Change: Same cc-list task note as another finding (not listed).
- other finding, minor, not in findings.json: GT adds an unrequested helper column 'Number of Days' (hidden) and hardcodes inconsistent formulas
  - Change: Same task note: the helper Number of Days column is not required.
