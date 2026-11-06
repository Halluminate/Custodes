# Changes: FINCH task-024

Fix summary (from the fix record):

The reference added an 'Average' block (AR1, AS1, A9, E9) to the original Scenario1 and Scenario2 sheets, against 'only the new sheet should be added'. Removed those 8 cells so the original sheets match the input. Scenario3 is unchanged. Full pass: the same unrequested Average block is now also cleared from Scenario3, and the guidance accepts Scenario3 charts with or without the contract price series the reference omits.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_24_ref_0.xlsx

## Fixed

- other finding, critical, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: files/gt/gt_24_ref_0.xlsx: cleared Scenario1 and Scenario2 AR1 ('Average'), AS1 (=SUM(AR4:AR63)/SUM(AC4:AC63)), A9 ('Average Price of Energy (7 x 24)') and E9 (=AS1). No formula or chart refers to them, and both sheets now equal the input in formulas and values. Scenario3 untouched
- other finding, major, not in findings.json: Ground truth workbook modifies original sheets (Scenario1 and Scenario2) and includes unrequested summary metrics (AR1, AS1, A9, E9) on Scenario3 despite prompt instructing to leave original sheets unchanged and mirror Scenario1
  - Change: files/gt/gt_24_ref_0.xlsx (on top of the critical fix): cleared Scenario3 AR1 ('Average'), AS1 (=SUM(AR4:AR63)/SUM(AC4:AC63)), A9 ('Average Price of Energy (7 x 24)') and E9 (=AS1), keeping the cell styles, and dropped their two calcChain entries, so Scenario3 mirrors Scenario1's layout like the cleaned Scenario1/2. No chart or other formula reads them; no other cell changed. (The Scenario1/Scenario2 part was already fixed under exploit-probe-1.)
- other finding, major, not in findings.json: The GT Scenario3 adds a weighted-average block that is not in Scenario1 (or Scenario2), so it does not strictly mirror Scenario1
  - Change: files/gt/gt_24_ref_0.xlsx (on top of the critical fix): cleared Scenario3 AR1 ('Average'), AS1 (=SUM(AR4:AR63)/SUM(AC4:AC63)), A9 ('Average Price of Energy (7 x 24)') and E9 (=AS1), keeping the cell styles, and dropped their two calcChain entries, so Scenario3 mirrors Scenario1's layout like the cleaned Scenario1/2. No chart or other formula reads them; no other cell changed.
- other finding, major, not in findings.json: Chart 1 (LineChart) in ground truth Scenario3 omits seasonal fixed price series (May-Sep and Q3) without specification in the prompt
  - Change: graderGuidance: added a task note after the opening paragraph that the reference Scenario3 price chart leaves out the May-Sep and Q3 fixed-price series, and that a Scenario3 chart area mirroring Scenario1's charts is accepted with or without contract series, including or omitting May-Sep and Q3.
- other finding, major, not in findings.json: The GT Scenario3 price chart leaves out the May-Sep and Q3 contract price series even though both are part of the allocation
  - Change: graderGuidance: added a task note after the opening paragraph that the reference Scenario3 price chart leaves out the May-Sep and Q3 fixed-price series, and that a Scenario3 chart area mirroring Scenario1's charts is accepted with or without contract series, including or omitting May-Sep and Q3.
