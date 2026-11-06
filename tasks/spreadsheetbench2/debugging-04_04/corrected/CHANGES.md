# Changes: SpreadsheetBench 2 debugging-04_04

Fix summary (from the fix record):

The answer key now also fixes the calculation errors QA named: the working-capital rows that mixed current-year receivables with prior-year inventory, payables and accrued expenses, and the one-year shift in projected interest. The projected unusual-item cells Income Statement J29:J31, J33 (anchored to random historical columns) have no single correct repair, so they are no longer graded. Checked with the real SB2 scorer (font_color mode, new answer_position): new golden vs itself 1.0; input + all key fixes (formulas and the 7 colours, written with openpyxl, no cached values) 1.0; input + only the 7 planted colour fixes 0.0 (mod 0.0355, 190 errors); untouched input 0.0.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_04_golden.xlsx

## Fixed

- [F1](../findings.json) (Verification): Broad audit instructions conflict with an answer key that preserves calculation errors
  - Change: gt_04_golden.xlsx: 'PP&E, Debt, NWC' C81:M83 now read the same-year Balance Sheet column as row 80 (D:N instead of C:M, e.g. I81 ='Balance Sheet'!J17), so I84 = 22.98 and DCF!C19 = -21.65; Income Statement J26:N26 now =-'PP&E, Debt, NWC'!D73 ... H73 (was E73 ... blank I73), so N26 carries the 2025 interest. Fonts untouched; all cached values recomputed with the verifier's LibreOffice recalc (38 formula cells changed, nothing else).
- [F2](../findings.json) (Verification): The prompt asks for a full audit, but only 7 font-colour cells are graded, and any other fix fails the whole task
  - Change: Same answer-key correction as 07150921 for the working-capital (I80 vs I81) error. The Income Statement J29 '=', J30 '=', J31 '=', J33 '=' anchors have no single defensible repair (zero hardcode in blue vs a consistent formula in black, and which year to anchor), so verifications[0].answer_position now skips 'Income Statement'!J29:J31 and J33 ('Income Statement'!B2:J57 -> B2:J28, B29:I33, J32, B34:J57); grader guidance range text updated to match.
