# Changes: SpreadsheetBench 2 template-01_04

Fix summary (from the fix record):

The cell check no longer grades the five 1/1/18 issue-date cells, so booking the 9,420 proceeds as an opening balance (golden) or as a day-1 change (the pattern the template's DTA/DTL rows use) both pass. Everything else is graded as before.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Issue-date column rejects the standard roll-forward (BOP 0, change +9,420), even though the template's DTA rows use exactly that pattern
  - Change: verifications[0].parameters.answer_position: 'OID_Bond'!B2:N37 split into 10 ranges that skip the 1/1/18 issue-date cells C16, C17, C29, C31, C32 (id, name, function, weight, mode unchanged). The golden books the 9,420 proceeds as BOP with a blank Change; the template's own DTA/DTL rows (C20=0, C24=0) suggest BOP 0 + Change 9,420, and both give the same EOP (C18, C33) that every later column uses. Checked with the real scorer: golden 1.0; golden with C16=0, C17=9420, C29=9420, C31=0, C32=9420 was 0.0 (reg 0.9920, mod 0.9789) and is now 1.0; untouched input still 0.0 (mod 0.0). graderGuidance range text updated.
- other finding, major, not in findings.json: Undisclosed structural and sign conventions in the OID bond template cause competent solutions to fail grading
  - Change: Same answer_position change for the Day-1 convention, the part that failed all three runs. The other conventions it lists follow from the template: the deferred-tax sign is fixed by GAAP tax = cash tax + deferred tax in rows 10-12, and the tax-basis loan/loss on extinguishment is cued by the L11 note, the B36 label and the seeded zeros in D32:I32 and D36:I36.
- other finding, major, not in findings.json: One-line instruction is graded all-or-nothing across about 100 changed cells whose conventions are never stated
  - Change: Same answer_position change (item c, the issue-date BOP/EOP). Items a, b, d follow from the template (cash tax = GAAP tax - deferred tax with no NOL row; L8 is the only free cell at the IRR label because M7 belongs to the cash-flow table; the tax loan treatment is cued by L11, B36 and the seeded zeros).
