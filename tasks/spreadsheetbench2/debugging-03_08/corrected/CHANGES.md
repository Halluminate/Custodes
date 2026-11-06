# Changes: SpreadsheetBench 2 debugging-03_08

Fix summary (from the fix record):

Full pass: the answer key also fixes the QA-named naming errors (LBO H31, J31:N31, Ex 10 B35) and the notes-repayment sign J67:N67; either sign convention for the '(-)' component rows now passes, and the cells with no single exact correction (Ex 13 G9:G28, Ex 10 B44) are not graded.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_03_golden.xlsx

## Fixed

- other finding, major, not in findings.json: The prompt asks for a broad audit, but the binary grader only accepts the sign-convention fixes and penalises other fixes it invites
  - Change: gt_03_golden.xlsx (XML-level, nothing else changed) now also fixes the QA-named naming errors with one defensible correction: LBO H31 '(S in millions)' -> '($ in millions)'; J31:N31 =TEXT(x$1,"#")&"E" -> &"P" to match J10:N10 (cached 2018P..2022P); 'Ex 10 - Forecast Assumptions '!B35 'amotization' -> 'amortization'. Ex 13 G14 (numeric 10.4 among text multiples) can be fixed by restyling G14 or by converting the whole column, so 'Ex 13 - Transaction Comps'!G9:G28 is left out of answer_position (B2:G30 -> B2:G8, B9:F28, B29:G30). Real SB2 scorer with the new answer_position: new golden 1.0; golden re-saved without caches (input + all key changes) 1.0; same with G14 restyled to '10.4×' and B44 at 35% 1.0; previous golden 0 (mod 0.9125); untouched input 0.
- other finding, major, not in findings.json: Only one of two valid sign-convention fixes passes; keeping explicit subtraction with positive '(-)' lines fails
  - Change: answer_position: 'LBO'!B1:V70 split so the sign-convention component rows J:N of rows 26, 36, 37, 38, 46, 56, 65 and 70 are not graded; the subtotals UFCF row 28, cash for debt service row 39, all debt balances and returns stay graded. A variant with the '(-)' lines made positive (J26 =J25, J36 =-(J46+J56+J65), J37 =J36*J20, J38 =$C$35*$C$37, J28/J39 kept as subtractions) now scores 1.0.
- other finding, minor, not in findings.json: Ground truth flips the senior notes repayment sign in the wrong direction (LBO row 67)
  - Change: gt_03_golden.xlsx LBO J67:N67 =+x58+x62 -> =x58-x62 (the input formula, matching J63 =J61-J62); cached values stay 0.
- other finding, minor, not in findings.json: Seed footnote misstates the pre-TCJA corporate tax rate
  - Change: The B44 footnote correction ('34%' -> '35%') can be worded in more than one way and is a whole-sentence exact-text cell, so 'Ex 10 - Forecast Assumptions '!B44 is left out of answer_position (B2:H50 -> B2:H43, C44:H44, B45:H50); fixing or keeping it now both pass.
