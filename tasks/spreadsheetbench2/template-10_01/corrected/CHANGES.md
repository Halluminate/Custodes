# Changes: SpreadsheetBench 2 template-10_01

Fix summary (from the fix record):

The golden fills pro forma share counts only in the Year 1 column (D39/D40 blank, D42 divides by C40), and filling the Year 2 share cells fails the regression check. One prompt sentence now states that layout.

Changed files (in this folder):

- prompt.md

## Fixed

- [F2](../findings.json) (Verification): Undisclosed empty-column constraint for Year 2 Pro Forma share counts (D39:D40) causes a two-column Pro Forma table to fail regression checks
  - Change: prompt.md: appended one sentence to the Instruction line: 'New Shares Issued and Total Pro Forma Shares are calculated once in the Year 1 column and used for both years, so leave the Year 2 cells of those two rows blank.' This states the GT's layout (C39/C40 filled, D39/D40 blank, D42 =D37/C40), which the all-or-nothing regression check enforces.
- [F1](../findings.json) (Verification): Grading fails a correct model if the Year 2 share rows (D39/D40) are filled in
  - Change: Same prompt sentence.
