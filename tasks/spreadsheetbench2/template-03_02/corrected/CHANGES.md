# Changes: SpreadsheetBench 2 template-03_02

Fix summary (from the fix record):

The answer key leaves fillable table cells blank (e.g. total assets C14/D14), so agents that fill them as told failed the regression check. I took those cells out of the graded range so either choice passes.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F1](../findings.json) (Verification): Instruction says to fill in all empty cells, but the answer key leaves cells blank that have clear non-zero values, and the grader fails any agent that fills them
  - Change: verifications[0].parameters.answer_position: 'M&A_Consolidation'!B2:F54 now excludes the cells the golden leaves blank although 'Fill in all empty cells' gives them clear values: C14:D14 (total assets 3,500 / 360), C28:D29 and E29 (NCI share / net income to parent by entity), D31:F31 (subsidiary, NCI and consolidated dividends). Agents may fill or leave them. Local check: golden PASS; golden with C14, D14, C29, D29, D31:F31 filled PASS (FAILED before, reg 0.9683). graderGuidance range updated to match.
- other finding, major, not in findings.json: The 'Less:' rows use inconsistent signs, and the key accepts only one of them
  - Change: verifications[0].parameters.answer_position: removed 'M&A_Consolidation'!E28:F28 (NCI share, sign convention not fixed by the sheet); F29 net income to parent (625.8) stays graded, so the NCI amount is still checked. graderGuidance range updated. Real scorer: golden PASS; golden with E28/F28 = -28.7 now PASS (was FAIL, mod 0.9545); untouched input FAIL (mod 0.0).

## Confirmed findings not fixed

- [F2](../findings.json): Grader rejects correctly completed parent and subsidiary asset totals
  - Reason: duplicate-of:F1
