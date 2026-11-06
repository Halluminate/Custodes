# Changes: SpreadsheetBench 2 debugging-03_02

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_03_golden.xlsx

## Fixed

- other finding, major, not in findings.json: Undisclosed scope of 'Embedded Hardcodes' edits vs. generic audit instruction causes unpenalized or penalized valid formula fixes on regression cells
  - Change: files/gt/gt_03_golden.xlsx (XML edits of these cells only; values unchanged, no other cell re-saved): LBO!J21:N21 1.8 -> ='Ex 10 - Forecast Assumptions '!D39..H39 (same pattern as J20:N20); LBO!H31 '(S in millions)' -> '($ in millions)'; LBO!J31:N31 &"E" -> &"P" (as J10:N10); LBO!V14 =-N69 -> =-(N44+N54+N63) (as Q14:U14); 'Ex 10 - Proj. Income Statement'!D11/D15 AVERAGE(...) -> ='Ex 10 - Forecast Assumptions '!D22 / D23 (as E11:H11, E15:H15); 'Ex 2 - Income Statement'!C18 =303.7 -> 303.7 (as D18:H18); 'Ex 10 - Forecast Assumptions '!D10:H10 -> =C13..G13 and D17:H17 -> =D11..H11. Named items with several equally valid formula texts are left out of answer_position: LBO!C33 (revolver rate: ='Ex 12 - Debt Schedule'!H9, =C28+C29 or =SUM(C28:C29)), LBO!C40 (notes rate: direct link or INDEX/MATCH like C39) and 'Ex 10 - Forecast Assumptions '!D13:H13 (roll-forward term order). Real scorer (formula mode, new answer_position): new key vs itself PASS; input plus all 46 key changes (21 planted + 25) PASS; untouched input FAIL (mod 0.0); old key FAIL (mod 0.4565).
- other finding, major, not in findings.json: Prompt asks for a broad audit, but the grader checks only 21 hardcode cells and penalises other valid fixes as regressions
  - Change: Same key and answer_position change as another finding (not listed) (C33, C40 ungraded; V14, H31, J31:N31, J21:N21 corrected in the key).
- other finding, minor, not in findings.json: Ground truth fixes only part of the embedded hardcodes, so its fix set is internally inconsistent
  - Change: Same change as another finding (not listed): C33 and C40 are left out of answer_position, so linking them (any form) or leaving them passes.
- other finding, major, not in findings.json: Regression checks penalize additional hardcode repairs requested by the task
  - Change: Same change as another finding (not listed): key D10:H10 =C13..G13 and D17:H17 =D11..H11; D13:H13 left out of answer_position.
