# Changes: SpreadsheetBench 2 debugging-03_06

Fix summary (from the fix record):

Answer key corrected for the QA-named errors with one defensible fix (TCJA interest-deduction cap in LBO!J37:N37, LBO!C33/C40 linked to the debt schedule, LBO!J31:N31 headers 'E'->'P'); the exit-year minimum cash LBO!Q15:V15 and its dependents left out of answer_position.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_03_golden.xlsx

## Fixed

- other finding, major, not in findings.json: The prompt asks for a broad audit, but the grader is all-or-nothing on cell values and only rewards the 4 planted reference fixes
  - Change: files/gt/gt_03_golden.xlsx (XML-level, same file as the TCJA fix): LBO!C33 0.053 -> ='Ex 12 - Debt Schedule'!H9 and C40 0.073 -> ='Ex 12 - Debt Schedule'!H11 (values unchanged); LBO!J31:N31 =TEXT(J$1,"#")&"E" -> &"P" (2018P..2022P, matching J10:N10, as in sibling <id>). verifications[0].parameters.answer_position (and the range list in graderGuidance): LBO!Q15:V15 with its dependents Q16:V16 and R19:V20 left out (constant 20.778 exit cash vs a per-year minimum cash are both defensible), as in siblings <id> and <id>. The Cover colour legend and other formatting are not compared in values mode, so no key change is needed for them; all-or-nothing scoring is the SB2 verifier's design and only parameters may change. Real SB2 scorer (new answer_position): new key vs itself 1.0; input plus every key change 1.0; input plus only the original planted fixes 0.0 (mod 0.58); untouched input 0.0.
- other finding, major, not in findings.json: Answer key ignores the fixture's stated interest-deduction cap
  - Change: files/gt/gt_03_golden.xlsx (XML-level, cached values from the verifier's LibreOffice recalc, nothing else changed): LBO!J37:M37 =+J36*-J20 -> =MIN(-J36,0.3*J13)*J20 (30% of EBITDA, 2018-2021) and N37 -> =MIN(-N36,0.3*N17)*N20 (30% of EBIT, 2022), as the 'Ex 10 - Forecast Assumptions ' footnote B45:B46 states. The cap binds in every year (2018: 124.18 interest vs 88.23 cap, shield 31.045 -> 22.058), so the carryforward is never usable inside the horizon and the result is unique. The debt sweep, interest and returns follow (75 cached values, e.g. LBO!V14 -1554.44 -> -1587.16, Valuation Bridge!C8 2082.99 -> 2050.27). Same edit and values as sibling task <id> (same golden). Real SB2 scorer (new answer_position): new key vs itself 1.0; input plus every key change 1.0; input plus only the original planted fixes 0.0 (mod 0.58); untouched input 0.0.
