# Changes: SpreadsheetBench 2 template-16_12

Fix summary (from the fix record):

Full pass: Valuation!C30 and C43 (ambiguous per-unit cells) removed from answer_position.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Per-unit C-column cells (C30, C43) in the GT use D/C6 instead of the '$/Unit/Month' basis D/(C6*12), so an agent that corrects them or follows the header fails the all-or-nothing verifier
  - Change: answer_position: 'Valuation'!B2:E43 split to leave out Valuation!C30 (seed '=D30/C6' is annual in the '$/Unit/Month' column; keeping it or correcting it to D30/(C6*12) are both defensible under 'ensure all formulas are correct') and C43 (GT value per unit D43/C6 vs per-unit-per-month header; no single defensible entry). Local SB2 scorer: golden PASS, untouched input FAIL (mod 0.0), golden with C30 corrected and C43 blank PASS (it failed under the old range).
- other finding, major, not in findings.json: Annual repairs expense is placed in the monthly expense column
  - Change: answer_position: 'Valuation'!B2:E43 split to leave out Valuation!C30 (seed '=D30/C6' is annual in the '$/Unit/Month' column; keeping it or correcting it to D30/(C6*12) are both defensible under 'ensure all formulas are correct') and C43 (GT value per unit D43/C6 vs per-unit-per-month header; no single defensible entry). Local SB2 scorer: golden PASS, untouched input FAIL (mod 0.0), golden with C30 corrected and C43 blank PASS (it failed under the old range).
