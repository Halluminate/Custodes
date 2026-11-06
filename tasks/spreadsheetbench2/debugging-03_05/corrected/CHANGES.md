# Changes: SpreadsheetBench 2 debugging-03_05

Fix summary (from the fix record):

Full pass: answer key extended with the QA-named label fixes (LBO H31 typo, J31:N31 header suffix, Forecast Assumptions B35 typo).

Changed files (in this folder):

- reference/gt_03_golden.xlsx

## Fixed

- other finding, major, not in findings.json: The prompt asks for a thorough audit, but the grader only rewards the two AVERAGE fixes and fails the run if more than about 8 other cell values change
  - Change: gt_03_golden.xlsx corrected at XML level for the QA-named label errors with one defensible fix (no value or formula elsewhere touched): LBO H31 '(S in millions)' -> '($ in millions)'; LBO J31:N31 =TEXT(x$1,"#")&"E" -> &"P" (cached 2018P..2022P, matching J10:N10 and R10:V10); 'Ex 10 - Forecast Assumptions '!B35 'Depreciation and amotization ...' -> 'Depreciation and amortization ...'. LBO V14 and Ex 2 C16/C18 are value-neutral, so values grading already accepts either form; not changed. answer_position unchanged. Real scorer: new golden PASS; input + the three AVERAGE fixes + the label fixes PASS; input + only the AVERAGE fixes now FAIL (mod 0.9314, H31/J31:N31/B35); untouched input FAIL (mod 0.0).
