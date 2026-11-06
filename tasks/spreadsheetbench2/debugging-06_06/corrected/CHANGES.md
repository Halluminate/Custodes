# Changes: SpreadsheetBench 2 debugging-06_06

Fix summary (from the fix record):

Audit task: the key now also fixes the QA-named errors with one defensible correction (Mohawk underutilization O76:Y76 hardwired to the Base row, FY2026 COGS rollup N101 dropping 47.1 of quarterly charges, SGA F118:S118 skipping Startup Costs, Operating Model F20 pulling amortization); the #NAME? rri CAGR cells and the unfinished PTA multiple block are no longer graded.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_06_golden.xlsx

## Fixed

- other finding, major, not in findings.json: Golden workbook leaves broken #NAME? formulas in Revenue Build!AC41 and AC43, penalizing agents that fix them
  - Change: files/gt/gt_06_golden.xlsx (XML formula edits on the original key; cached values set only for the cells whose LibreOffice recalc changed, 104 cells, nothing else touched): 'Supporting Schedules'!O76:Y76 ...-O80 -> ...-O77 (current, scenario-selected utilization, as N76 uses N77; O80 is the hardwired Base row); 'Supporting Schedules'!F118:S118 =SUM(F112,F117) -> =SUM(F112,F116:F117) (the '(+) Startup Costs' row, like COGS row 103 =SUM(F96,F100:F101)); 'Operating Model'!F20 ='IS Ann'!C28 (Amort. of Goodwill) -> ='IS Ann'!C29 (Other Operating Expense, as G20:I20). answer_position: 'Revenue Build'!AC41 and AC43 (=rri(5,W41,AA41) #NAME? in input and key) left out: RRI over years 1..5 can be repaired with 5 or 4 periods (0.3797 vs 0.4953), no single correction. PTA!R22, R25, R26 and dependents R28, R32, R35, R38, R39 left out: an unfinished block (R24 multiple blank, 'Try to find EBIT') with no single repair. Supporting Schedules F40:I40 (quarterly BS links in an annual schedule) are kept as in the key: opening FY2022 PP&E is not in 'BS Ann', the annual mapping has more than one reading, and dropping its cascade would un-grade the whole forecast, DCF and Cover, including the planted DCF!E10 fix. Real SB2 scorer: new key 1.0; input + all key changes 1.0; input + only the 4 planted fixes 0.0 (mod 0.5628); untouched input 0.0.
- other finding, major, not in findings.json: Golden workbook preserves an incorrect annual COGS rollup and rejects its repair
  - Change: Same key file: 'Supporting Schedules'!N101 =SUM(N94,N95) -> =SUM(J101:M101), so FY2026 annual 'Other Irregular Expenses' carries the quarterly 47.1 (J101) like N96 =SUM(J96:M96); N103 532.23 -> 579.33 = SUM(J103:M103) with the O76 fix applied. Cascade (Operating Model J7 onward, DCF, Cover!G10 1.635 -> 1.385) recomputed by the verifier's LibreOffice recalc.
