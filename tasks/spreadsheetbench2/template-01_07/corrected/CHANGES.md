# Changes: SpreadsheetBench 2 template-01_07

Fix summary (from the fix record):

Added one sentence to the instruction stating the two template conventions the answer key uses and the trials missed: row 28 totals the DTA and DTL balances, and the tax-basis loan is carried at the $30,000 face value. The missing-openpyxl finding is a sandbox issue. Full pass: C29:H29 (blank in the key, 'fill all empty cells' in the instruction) left out of the cell check.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F1](../findings.json) (Task Spec): Multiple undisclosed accounting, layout, and sign conventions in the template cause ambiguous grading and contradict the ground truth
  - Change: prompt.md: after 'Fill in all empty cells.' added: 'Row 28 is the total of the deferred tax asset and liability balances, and the tax-basis loan balance in rows 31 to 33 stays at the $30,000 face value.' Matches golden C28:H28 (=C22+C26) and C31:H31 = 30000.
- other finding, major, not in findings.json: 'Fill in all empty cells' contradicts both the GT and the 'do not alter cells with values' rule
  - Change: verifications[0].parameters.answer_position: "'BondAccounting'!B2:L37" -> "'BondAccounting'!B2:L28,'BondAccounting'!B29,'BondAccounting'!I29:L29,'BondAccounting'!B30:L37" (drops C29:H29, the Tax B/S 'Change in cash' cells the key leaves blank although the instruction says to fill every empty cell, so a -900 coupon outflow there no longer fails); graderGuidance range text updated. Real scorer: golden PASS; golden with C29:H29=-900 FAIL before, PASS after; untouched input FAIL (mod=0).
