# Changes: SpreadsheetBench 2 financial-model-16_04

Fix summary (from the fix record):

No change. The ungraded seed chart cannot be fixed with the cell-check verifier. The other findings are false or infra.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, minor, not in findings.json: Seed workbook contains broken valuation sensitivity references
  - Change: Relabelled true after a real-scorer check: the golden fails its own SB2 check on the 48 '=assumptions!#ref!' cells in 'Valuation Summary and Football'!L32:S37 (recalc gives #REF! vs cached #NAME?). Those cells are left out of answer_position (same as Ramjet 16_03/16_05), guidance range text updated.
