# Changes: SpreadsheetBench 2 template-06_14

Fix summary (from the fix record):

SB2 cell check: the 24 growth cells with no prior period (blank in the golden) are left out of answer_position, so an 'N/A' placeholder there no longer fails the whole task. Golden still scores 1.0, untouched input still fails.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: All-or-nothing grading fails the whole task if the agent fills any cell the answer key leaves blank, such as a common 'N/A' placeholder
  - Change: verifications[0].parameters.answer_position: 'SegmentRevenue'!B2:L25 -> the same block minus C12, G12, L12, C13:G13, C19, G19, L19, C20:G20, C24, G24, L24, C25:G25 (no-prior-period growth cells the golden leaves blank). id/name/function/weight/mode unchanged. Re-scored with the real SB2 scorer.
