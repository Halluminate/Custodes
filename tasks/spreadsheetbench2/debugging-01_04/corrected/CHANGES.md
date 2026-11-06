# Changes: SpreadsheetBench 2 debugging-01_04

Fix summary (from the fix record):

The golden cached stale What-If iteration values (e.g. LBO C11 18.2 for =+C20 = 14.2), so it failed its own recalculating check; those 65 caches now hold the values the formulas give. The four sensitivity grids, which are TABLE() formulas caching one meaningless constant in the GT and '=#VALUE!' in the input, are dropped from answer_position. For the 'audit thoroughly' findings, the key now also fixes the Ex 5 Downside cohorts and the Downside margin formulas. Cells QA named that have no single valid repair (the #DIV/0! ratios, the 0/0 margins and colour cells whose convention the workbook never states) are no longer graded.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_01_golden.xlsx

## Fixed

- [F8](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells is a trivial fail (cannot pass even on gt_01_golden.xlsx) because it compares LibreOffice-recalculated agent output against un-recalculated stale cached values in gt_path
  - Change: gt_01_golden.xlsx: cached values of 65 formula cells (Ex 1 - LBO 34, Ex 2 - Valuation Bridge 3, Ex 5 - M&A 28) replaced with the values the formulas actually give (LibreOffice recalculation, stable on a second pass), e.g. 'Ex 1 - LBO'!C11 18.2034 -> 14.2034, C32 109.5182 -> 101.3452, U41 0.137 -> 0.092; formulas, font colors and all other cells unchanged (XML <v> edit only). Local grade with the real verifier: new golden 1.0/1.0 (was mod 0.6597, 65 errors).
- [F7](../findings.json) (Verification): Golden gate: the ground-truth deliverable does not score full reward
  - Change: Same GT cache correction; golden scores 1.0.
- [F4](../findings.json) (Verification): Golden workbook contains stale un-recalculated cached values from an Excel What-If Data Table iteration while the verifier only recalculates the agent's output in LibreOffice
  - Change: Same GT cache correction: the GT now holds the true values (C11 14.2034) that a recalculated output reproduces.
- [F2](../findings.json) (Verification): The ground truth fails its own verifier: its cached values don't match its formulas, so no output can pass
  - Change: Same GT cache correction (C11, C32 and every other inconsistent cache now match their formulas).
- [F5](../findings.json) (Environment & Infra): The input workbook also has stale cached values that differ from both the GT and the true results, which turns about 65 unchanged formula cells into graded 'modification' cells
  - Change: Same GT cache correction: the unchanged formula cells that differ only by the input's stale cache are still modification cells, but they now demand the recalculated value (e.g. C11 14.2034), which any output reproduces after the grader's recalculation.
- [F3](../findings.json) (Verification): Data-table sensitivity cells were replaced with '=#VALUE!' and the GT's 'answer' is a meaningless constant
  - Change: Verifier parameter answer_position: "'Ex 1 - LBO'!B1:AK95" split into B1:AF95, AG1:AK17, AG23:AK26, AG32:AK35, AG41:AK44, AG50:AK95, dropping only the four 5x5 What-If grids AG18:AK22, AG27:AK31, AG36:AK40, AG45:AK49 (=TABLE() in the GT, all caching '2.4x/19%'; '=#VALUE!' in the input). Same range change in grader_guidance.md. An openpyxl-saved copy of the golden now scores 1.0/1.0 (mod 0.4974 with 100 grid errors under the old ranges).
- [F6](../findings.json) (Verification): Inconsistent golden caches cause the golden workbook itself to fail grading
  - Change: Same GT cache correction (C32 101.3452, U41 0.092).
- [F1](../findings.json) (Verification): Sensitivity answer grids contain identical base-case results instead of scenario results
  - Change: Same answer_position change: the four sensitivity grids holding one constant are no longer graded.
- other finding, major, not in findings.json: Grading treats genuine financial-model repairs as prohibited regressions
  - Change: gt_01_golden.xlsx 'Ex 5 - M&A': Downside cohorts Z58:AB58, AA59:AB59 and AB60 now use the Downside counts $Z33/$AA33/$AB33 (they used Upside $S33/$T33/$U33). Only the Ex 5 cells whose recalculated value changed got new caches. The 15 #DIV/0! cells E43:G43, D53:G53, D63:G63, D73:G73 have more than one valid repair (guard with IFERROR, or relink the hardcoded case C4), so they are left out of answer_position. Checked with the real SB2 scorer (font_color mode): new key 1.0, untouched input plus all key changes (formulas and the 32 planted colours) 1.0, the prepared key with only these formula edits applied and recalculated 1.0, untouched input 0.0.
- other finding, major, not in findings.json: Task prompt uses generic open-ended model audit instructions while the ground truth only updates 30 font-color cells and leaves multiple real formula bugs untouched
  - Change: gt_01_golden.xlsx 'Ex 5 - M&A': the same Downside cohort fix, and the Downside '% Margin' rows Y53:AB53, Y63:AB63, Y73:AB73 now =+IFERROR(Y52/Y42,"N/A") etc. (they computed YoY growth). The Downside block has no revenue, so the repaired margins are 0/0, where 'N/A' and #DIV/0! are equally valid, and those 12 cells are left out of answer_position. The colour cells QA named ('Ex 1 - LBO'!C33, C35, P33:U33, Q54:U55, Q58:U59, 'Ex 2 - Valuation Bridge'!C3:C7) are also left out. The workbook never states its colour convention and keeps most such cells black, so no single recolouring is defensible. Checked with the real SB2 scorer (font_color mode): new key 1.0, untouched input plus all key changes (formulas and the 32 planted colours) 1.0, the prepared key with only these formula edits applied and recalculated 1.0, untouched input 0.0.
