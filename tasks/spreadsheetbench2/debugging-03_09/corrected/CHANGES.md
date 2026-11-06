# Changes: SpreadsheetBench 2 debugging-03_09

Fix summary (from the fix record):

The answer key now applies the TCJA interest-deduction cap the workbook states (LBO J37:N37), the extra error QA named; the exit-cash cells Q15:V15 and their MOIC/IRR dependents, which have no single repair, are no longer graded. Real SB2 scorer: new golden 1.0; input + every key change 1.0 (also with exit cash 20.778 filled); input + only the planted reference fixes 0.0 (mod 0.2241); untouched input 0.0.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_03_golden.xlsx

## Fixed

- other finding, major, not in findings.json: Open-ended 'audit thoroughly' task is graded all-or-nothing against a key that fixes only 3 reference errors, so other valid fixes fail
  - Change: files/gt/gt_03_golden.xlsx (XML-level, cached values from the verifier's LibreOffice recalc, nothing else changed): 'LBO'!J37:M37 =+J36*-J20 -> =MIN(-J36,0.3*J13)*J20 (30% of EBITDA, 2018-2021) and N37 -> =MIN(-N36,0.3*N17)*N20 (30% of EBIT, 2022), as the 'Ex 10 - Forecast Assumptions ' footnote B45:B46 states. The cap binds in every year (2018: 124.18 interest vs 88.23 cap, shield 31.05 -> 22.06), so the indefinite carryforward is never usable inside the horizon and the result is unique. The debt sweep, interest and returns cascade follow (V14 -1554.44 -> -1587.16, V20 0.210 -> 0.206). Item (2): 'LBO'!Q15:V15 with dependents Q16:V16 and R19:V20 left out of answer_position (constant 20.778 vs per-year 1% of revenue are both defensible), as in sibling task <id>. Real SB2 scorer: new golden 1.0; input + every key change 1.0, and 1.0 with exit cash 20.778 filled; input + only the planted fixes 0.0; untouched input 0.0.
- other finding, major, not in findings.json: Answer key penalizes applying the workbook’s stated interest-deduction cap
  - Change: files/gt/gt_03_golden.xlsx (XML-level, cached values from the verifier's LibreOffice recalc, nothing else changed): 'LBO'!J37:M37 =+J36*-J20 -> =MIN(-J36,0.3*J13)*J20 (30% of EBITDA, 2018-2021) and N37 -> =MIN(-N36,0.3*N17)*N20 (30% of EBIT, 2022), as the 'Ex 10 - Forecast Assumptions ' footnote B45:B46 states. The cap binds in every year (2018: 124.18 interest vs 88.23 cap, shield 31.05 -> 22.06), so the indefinite carryforward is never usable inside the horizon and the result is unique. The debt sweep, interest and returns cascade follow (V14 -1554.44 -> -1587.16, V20 0.210 -> 0.206).
