# Changes: SpreadsheetBench 2 financial-model-02_03

Fix summary (from the fix record):

The prompt now asks for AP as a % of COGS (matching the sheet label and the model's AP forecast formulas) on end-of-period balances, and the answer key's FY20/FY21 AP ratios now use ending AP like FY19 instead of an undisclosed average. The golden was recalculated in LibreOffice. Full pass: the key AR % of sales forecast H10:J10 now uses the same 3-year rolling window as inventory, AP and the seeded tax rate.

Changed files (in this folder):

- prompt.md
- reference/gt_02_PP_golden.xlsx

## Fixed

- [F1](../findings.json) (Task Spec): Instruction asks for Accounts Payable (AP) as a percentage of Sales, contradicting the worksheet label and golden workbook which compute AP as a % of COGS using a mixed EOP/average formula
  - Change: Prompt sentence changed from 'Accounts Receivable (AR) and Accounts Payable (AP) as percentages of Sales, and then Inventory as a % of COGS for all periods.' to 'Accounts Receivable (AR) as a % of Sales, and then Inventory and Accounts Payable (AP) as a % of COGS for all periods, using end-of-period balances.'. gt_02_PP_golden.xlsx 'BS schedules'!E27 and F27 changed from the average-AP formulas to =('IS,BS,CF'!F86/'IS,BS,CF'!F22)*-1 and =('IS,BS,CF'!G86/'IS,BS,CF'!G22)*-1 (same pattern as D27). The file was recalculated with the verifier's LibreOffice pipeline, so G27:J27, G25:J25 and the downstream statements carry the new values. Checked: the corrected golden scores 1.0 against the new key both with cached values and saved by openpyxl without caches.
- [F3](../findings.json) (Task Spec): Prompt says AP should be a % of Sales, but the sheet label and GT use % of COGS
  - Change: Same prompt sentence fix (AP as a % of COGS) plus the E27/F27 key fix.
- [F2](../findings.json) (Verification): Graded AP calculation contradicts the task's requested denominator
  - Change: Same: the prompt's denominator now matches the key, and the key uses one consistent end-of-period AP/COGS ratio.
- other finding, major, not in findings.json: Undisclosed forecast averaging window conventions for working capital percentages in BS schedules (4-year window in H10 vs. 3-year rolling window elsewhere)
  - Change: gt_02_PP_golden.xlsx 'BS schedules'!H10:J10 changed from =AVERAGE(D10:G10), =AVERAGE(E10:H10), =AVERAGE(F10:I10) to 3-year rolling =AVERAGE(E10:G10), =AVERAGE(F10:H10), =AVERAGE(G10:I10), the same window as the key's inventory (row 18) and AP (row 27) rows and the seeded tax-rate row 145. Formulas edited in the XML only; cached values from the verifier's LibreOffice recalc injected for the 40 cells that moved (H10:J10, AR rows 6-8, DSO, cash/CF/ratios), nothing else changed. Real SB2 scorer (unchanged answer_position): new golden 1.0, golden re-saved without caches 1.0, previous golden 0 (mod 0.886), untouched input 0.
- other finding, major, not in findings.json: AR % of sales forecast uses an arbitrary, inconsistent averaging window that the binary grader requires exactly
  - Change: Same AR window fix in the key as another finding (not listed).
- other finding, major, not in findings.json: Forecast working-capital assumptions required by the answer key are not supplied
  - Change: Same AR window fix in the key as another finding (not listed).
