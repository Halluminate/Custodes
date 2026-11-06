# Changes: SpreadsheetBench 2 financial-model-06_02

Fix summary (from the fix record):

The prompt said 'Depreciation Rate at 1% monthly' while the answer key, like the model's Amortisation row, charges the annual rate /12 each month, and the key's depreciation formula pointed at the Capex % row. I reworded that one prompt sentence to state the rate/12 convention and pointed the key's L13:BS13 at the Depreciation Rate row (values unchanged).

Changed files (in this folder):

- prompt.md
- reference/gt_06_DigiMark_golden.xlsx

## Fixed

- [F2](../findings.json) (Task Spec): Contradictory instruction and broken ground truth formula for Depreciation Rate ('1% monthly' vs 1%/12 referencing Capex row 17)
  - Change: Prompt: the depreciation sentence now reads "In the Balance Sheet Schedules, set the annual Depreciation Rate at 1% in each month from Apr-25 to Mar-30, then calculate monthly Depreciation (rate/12, as in the Amortisation row) and Net Block for all months." so it states the rate/12 monthly charge the answer key (and the model's own Amortisation row) uses. gt_06_DigiMark_golden.xlsx: 'Balancesheet Schedules'!L13:BS13 now reference row 18 (Depreciation Rate) instead of row 17 (Capex as % of Revenue), =SUM(L11:L12)*-L18/12; both rows hold 0.01 so no value changes (formula text edited in the XML, cached values kept; local grade of the patched golden 1.0).
- [F3](../findings.json) (Task Spec): "1% monthly" depreciation wording conflicts with the answer key, which uses 1%/12 per month, and the grader is all-or-nothing
  - Change: Prompt: the depreciation sentence now reads "In the Balance Sheet Schedules, set the annual Depreciation Rate at 1% in each month from Apr-25 to Mar-30, then calculate monthly Depreciation (rate/12, as in the Amortisation row) and Net Block for all months." so it states the rate/12 monthly charge the answer key (and the model's own Amortisation row) uses.
- [F1](../findings.json) (Verification): Answer key calculates annual rather than monthly 1% depreciation
  - Change: Prompt: the depreciation sentence now reads "In the Balance Sheet Schedules, set the annual Depreciation Rate at 1% in each month from Apr-25 to Mar-30, then calculate monthly Depreciation (rate/12, as in the Amortisation row) and Net Block for all months." so it states the rate/12 monthly charge the answer key (and the model's own Amortisation row) uses. gt_06_DigiMark_golden.xlsx: 'Balancesheet Schedules'!L13:BS13 now reference row 18 (Depreciation Rate) instead of row 17 (Capex as % of Revenue), =SUM(L11:L12)*-L18/12; both rows hold 0.01 so no value changes (formula text edited in the XML, cached values kept; local grade of the patched golden 1.0).
