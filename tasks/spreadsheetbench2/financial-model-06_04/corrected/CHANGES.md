# Changes: SpreadsheetBench 2 financial-model-06_04

Fix summary (from the fix record):

Rebuilt the golden's DCF sensitivity grid (DCF!N18:R22) from the golden's own DCF model, so a correctly built table now matches. The missing-openpyxl finding is environment infrastructure. Full pass: the prompt now states how Net Cost of Equity applies the liquidity discount and premium, and the cell check no longer grades the data-table corner M17.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_06_DigiMark_golden.xlsx

## Fixed

- [F1](../findings.json) (Verification): DCF sensitivity table ground truth values (DCF!N18:R22) are stale hardcoded numbers from a different model version that contradict the workbook's own DCF formulas
  - Change: Golden gt_06_DigiMark_golden.xlsx: replaced the 25 stale hardcoded sensitivity values in DCF!N18:R22 with the golden's own DCF (C24 = PV of C16:G16 + PV of terminal H12+H13 + net debt C23) evaluated at each WACC in M18:M22 and terminal growth in N17:R17. The method reproduces the base case C24 = 44,371,232.57 exactly. Examples: N18 28,267,200 -> 34,026,690, P20 26,461,332 -> 32,031,965, R22 24,815,330 -> 30,220,519. Direct XML edit, so no other cell changed. The patched golden grades 1.0 locally.
- [F2](../findings.json) (Verification): The ground-truth sensitivity table values can't be reproduced from the GT's own DCF, so a correctly built table always fails
  - Change: Golden gt_06_DigiMark_golden.xlsx: replaced the 25 stale hardcoded sensitivity values in DCF!N18:R22 with the golden's own DCF (C24 = PV of C16:G16 + PV of terminal H12+H13 + net debt C23) evaluated at each WACC in M18:M22 and terminal growth in N17:R17. The method reproduces the base case C24 = 44,371,232.57 exactly. Examples: N18 28,267,200 -> 34,026,690, P20 26,461,332 -> 32,031,965, R22 24,815,330 -> 30,220,519. Direct XML edit, so no other cell changed. The patched golden grades 1.0 locally.
- [F3](../findings.json) (Verification): Sensitivity answer key does not match the supplied DCF model
  - Change: Golden gt_06_DigiMark_golden.xlsx: replaced the 25 stale hardcoded sensitivity values in DCF!N18:R22 with the golden's own DCF (C24 = PV of C16:G16 + PV of terminal H12+H13 + net debt C23) evaluated at each WACC in M18:M22 and terminal growth in N17:R17. The method reproduces the base case C24 = 44,371,232.57 exactly. Examples: N18 28,267,200 -> 34,026,690, P20 26,461,332 -> 32,031,965, R22 24,815,330 -> 30,220,519. Direct XML edit, so no other cell changed. The patched golden grades 1.0 locally.
- other finding, major, not in findings.json: Instruction to 'calculate Net Cost of Equity using CAPM' in DCF!C45 is misleading and does not disclose how Liquidity discount (C43) is applied
  - Change: prompt.md: the DCF sentence now reads 'In the DCF sheet, calculate Net Cost of Equity as the CAPM Cost of Equity increased by the Liquidity discount (Cost of Equity × (1 + Liquidity discount)) plus the Company Specific premium, then calculate Equity Value – Pre Money, then create a sensitivity table using Terminal Growth Rate and WACC ranges.', matching GT C45 =C42*(1+C43)+C44 (CAPM Cost of Equity is already in C42; an additive build-up C42+C43+C44 would otherwise be equally defensible and fails the all-or-nothing check).
- other finding, major, not in findings.json: The Net Cost of Equity formula is not specified, and the GT's multiplicative liquidity adjustment is only one valid reading
  - Change: Same prompt DCF sentence change as another finding (not listed).
- other finding, major, not in findings.json: The sensitivity table layout and units are unstated but graded: the corner cell M17 must link to Post-Money equity, and the values must be raw USD despite the 'USD in millions' title
  - Change: verifications[0].answer_position: 'DCF'!B2:R58 -> 'DCF'!B2:L58,'DCF'!M2:M16,'DCF'!M18:M58,'DCF'!N2:R58 (drops only the data-table corner M17 =C24, a convention the prompt never asks for); graderGuidance range updated. The units half of the finding is not a defect: the model's own C24 is in raw USD and the grid follows it. Real scorer: patched golden PASS, input+key changes PASS, input+key changes with M17 blank PASS (was FAIL on M17), untouched input FAIL.
