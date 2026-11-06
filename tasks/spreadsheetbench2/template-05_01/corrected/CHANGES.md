# Changes: SpreadsheetBench 2 template-05_01

Fix summary (from the fix record):

2020 balance-sheet totals C23/C29 left out of grading, so filling them (as 'fill all empty cells' asks) or leaving them blank (as the key does) both pass.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Instruction to fill 'all empty cells in the ... Balance Sheet ...' is ambiguous regarding 2020 total cells C23 and C29, which the ground truth leaves blank
  - Change: answer_position 'DeferredTax'!B2:I51 -> "'DeferredTax'!B2:I22,'DeferredTax'!B23,'DeferredTax'!D23:I23,'DeferredTax'!B24:I28,'DeferredTax'!B29,'DeferredTax'!D29:I29,'DeferredTax'!B30:I51" (drops C23 and C29 only). Real scorer: golden 1.0/1.0; golden plus C23 =SUM(C19:C22), C29 =SUM(C26:C28) 1.0/1.0 (was reg 0.9942 = fail); untouched input fails (mod 0.0). graderGuidance updated.
- other finding, major, not in findings.json: "Fill all empty cells" also covers 2020 Balance Sheet totals that the answer key leaves blank, and the grading is all-or-nothing
  - Change: answer_position 'DeferredTax'!B2:I51 -> "'DeferredTax'!B2:I22,'DeferredTax'!B23,'DeferredTax'!D23:I23,'DeferredTax'!B24:I28,'DeferredTax'!B29,'DeferredTax'!D29:I29,'DeferredTax'!B30:I51" (drops C23 and C29 only). Real scorer: golden 1.0/1.0; golden plus C23 =SUM(C19:C22), C29 =SUM(C26:C28) 1.0/1.0 (was reg 0.9942 = fail); untouched input fails (mod 0.0). graderGuidance updated.
- other finding, major, not in findings.json: Correct opening balance-sheet totals are penalized despite the instruction to fill all empty cells
  - Change: answer_position 'DeferredTax'!B2:I51 -> "'DeferredTax'!B2:I22,'DeferredTax'!B23,'DeferredTax'!D23:I23,'DeferredTax'!B24:I28,'DeferredTax'!B29,'DeferredTax'!D29:I29,'DeferredTax'!B30:I51" (drops C23 and C29 only). Real scorer: golden 1.0/1.0; golden plus C23 =SUM(C19:C22), C29 =SUM(C26:C28) 1.0/1.0 (was reg 0.9942 = fail); untouched input fails (mod 0.0). graderGuidance updated.
