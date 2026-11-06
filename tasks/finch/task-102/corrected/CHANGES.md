# Changes: FINCH task-102

Fix summary (from the fix record):

The answer key's Transfer totals row lacked the Total Net and a label although the prompt asks for Total Longs, Total Shorts and Total Net at the bottom; the key now has B40 'Total' and F40 =SUM(F4:F39) (-21). The grader is also told that the key's 35-month zero-filled strip (with its V3 gap) is one acceptable month layout, since the prompt only asks to cover the months present.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_102_ref_0.xlsx

## Fixed

- other finding, major, not in findings.json: Ground-truth workbook omits required Total Net and total row labels on the Transfer worksheet
  - Change: gt_102_ref_0.xlsx Transfer row 40: added B40 'Total' (inline string, same style s=2 as the month labels) and F40 =SUM(F4:F39) with cached -21. Edited at the XML level; every other cell, formula and style unchanged. LibreOffice recalc gives Total,40,61,,-21.
- other finding, major, not in findings.json: GT is missing the Total Net and the total-row labels the prompt asks for
  - Change: Same GT change as another finding (not listed): Total Net -21 and a 'Total' label now sit in the totals row.
- other finding, major, not in findings.json: Undisclosed and irregular 35-month NYMEX delivery sequence (Z through X3 with V3 omitted) in ground truth vs. only Z and F1 present in source workbook
  - Change: grader_guidance.md: one sentence added to the task preamble saying the reference's Z..X3 strip is one acceptable layout and that any Z, F1… list covering the months present (Z, F1) with 0 for months without data is equivalent; extra zero rows need not match row for row. Official judge text unchanged.
- other finding, major, not in findings.json: 'Covering all months present' conflicts with the GT's fixed 3-year strip of 35 months
  - Change: Same guidance sentence as another finding (not listed).
- other finding, minor, not in findings.json: GT month sequence is broken: V3 and Z3 are missing and row 39 is blank but carries formulas
  - Change: Same guidance sentence: it names the key's V3 gap and unlabeled zero row so the grader does not demand a row-for-row match with that broken strip.
