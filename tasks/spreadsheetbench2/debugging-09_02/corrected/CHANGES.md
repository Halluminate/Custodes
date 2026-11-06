# Changes: SpreadsheetBench 2 debugging-09_02

Fix summary (from the fix record):

The key keeps 82 embedded growth and case-spread constants of the planted class as regression cells. Those cells, which have no single correction, are no longer graded.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Prompt asks for a broad audit but the grader accepts only 8 hardcode fixes and fails runs that fix more than ~13 other cells (output_scope_mismatch)
  - Change: verifications[0].parameters.answer_position (+ graderGuidance range list): the named embedded constants with no single correction (no defined input cell for the growth rates and case spreads) are left out: Financials!J10:N11 and 'Operating Cases'!G13:N14, G21:N22, G29:N30, G37:N39. New ranges: 'LBO'!A2:X218,'Financials'!A2:Q9,'Financials'!A10:I11,'Financials'!O10:Q11,'Financials'!A12:Q29,'Operating Cases'!A2:Q12,'Operating Cases'!A13:F14,'Operating Cases'!O13:Q14,'Operating Cases'!A15:Q20,'Operating Cases'!A21:F22,'Operating Cases'!O21:Q22,'Operating Cases'!A23:Q28,'Operating Cases'!A29:F30,'Operating Cases'!O29:Q30,'Operating Cases'!A31:Q36,'Operating Cases'!A37:F39,'Operating Cases'!O37:Q39,'Operating Cases'!A40:Q47. Real scorer (formula mode): golden 1.0 (reg 1.0, mod 1.0); untouched input 0.0 (mod 0.0); golden with those 82 formulas rewritten fails under the old ranges (reg 0.9873) and passes under the new ones (1.0).
