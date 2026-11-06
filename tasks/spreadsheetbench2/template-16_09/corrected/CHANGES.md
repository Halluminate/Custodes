# Changes: SpreadsheetBench 2 template-16_09

Fix summary (from the fix record):

16_09: the key's per-SF metrics are monthly although column H only says /SF, the unlabeled H42 is graded as an NOI margin, and the TODAY() cells in Occupancy_Data fail on any later date. One instruction sentence now states the monthly /SF convention, and H42 and Occupancy_Data!A3:A4 are left out of answer_position.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Undisclosed monthly (/SF/Mo) unit convention in Valuation!H10:H26 where header specifies /SF
  - Change: prompt.md: after 'Ensure that all formulas, references, and calculations are correct.' added: The /SF metrics in Valuation column H are monthly amounts per square foot of total suite area (Suites times Average Suite Size), as in the occupancy report. Matches GT H10:H26 (=Ir/($C$4*$C$5)/12, e.g. H10 3.219 vs Occupancy_Data F12 3.22).
- other finding, major, not in findings.json: The whole 'Metrics' column (H) is graded, but the task never asks for it, and the /SF convention (monthly) is only implied
  - Change: Same instruction sentence as another finding (not listed) (monthly /SF convention for column H). The /Suite/Yr rows are already labelled.
- other finding, major, not in findings.json: Unlabeled metric cell Valuation!H42 on NET OPERATING INCOME row graded as NOI margin (=I42/I26)
  - Change: verifications[0].parameters.answer_position: "'Valuation'!B2:P46,'Occupancy_Data'!A1:Q12" -> "'Valuation'!B2:P41,'Valuation'!B42:G42,'Valuation'!I42:P42,'Valuation'!B43:P46,'Occupancy_Data'!A1:Q2,'Occupancy_Data'!B3:Q4,'Occupancy_Data'!A5:Q12" (drops Valuation!H42, the unlabeled cell the key fills with NOI/EGR, which has no single defensible value). graderGuidance range note added. Real scorer with the new answer_position: golden PASS reg 1.0 mod 1.0 with 0 errors (before: 1 regression error at Occupancy_Data!A4), golden with H42 blank PASS, untouched input FAIL (mod 0.0, 48 errors).
- other finding, major, not in findings.json: Binary verifier requires an unlabeled NOI-margin value in Valuation!H42 that nothing in the sheet points to
  - Change: Same answer_position change as another finding (not listed) (H42 no longer compared).
- other finding, major, not in findings.json: Volatile TODAY() formulas in Occupancy_Data!A3:A4 included in answer_position cause automatic regression errors upon recalculation
  - Change: verifications[0].parameters.answer_position: "'Valuation'!B2:P46,'Occupancy_Data'!A1:Q12" -> "'Valuation'!B2:P41,'Valuation'!B42:G42,'Valuation'!I42:P42,'Valuation'!B43:P46,'Occupancy_Data'!A1:Q2,'Occupancy_Data'!B3:Q4,'Occupancy_Data'!A5:Q12" (drops Occupancy_Data!A3 =TODAY() and A4 'As of Date' text, which change with the grading date). Real scorer with the new answer_position: golden PASS reg 1.0 mod 1.0 with 0 errors (before: 1 regression error at Occupancy_Data!A4), golden with H42 blank PASS, untouched input FAIL (mod 0.0, 48 errors).
- other finding, major, not in findings.json: Graded regression range includes volatile TODAY() cells, which uses up the regression error budget
  - Change: Same answer_position change as another finding (not listed) (A3:A4 no longer use the regression budget).
- other finding, major, not in findings.json: SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells falsely fails Unit 1 due to unstated monthly /SF/Mo division in H10:H26, unlabeled H42, and un-recalculated TODAY() in Occupancy_Data!A4
  - Change: Covered by the three changes above: the /SF sentence (another finding (not listed)), H42 dropped (another finding (not listed)) and Occupancy_Data!A3:A4 dropped (another finding (not listed)).
