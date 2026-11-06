# Changes: SpreadsheetBench 2 financial-model-18_04

Fix summary (from the fix record):

Removed the unrequested 'Esc. %' label from P&L!A13 in the answer key. Revenue prompt sentence now describes the per-column 1.02 escalation the key uses.

Changed files (in this folder):

- prompt.md
- reference/gt_18_RoadAssets_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check gives false negative (score 0.0) on Units 2 and 3 due to uninstructed golden cell P&L!A13 = 'Esc. %'
  - Change: gt_18_RoadAssets_golden.xlsx: cleared the unrequested label at P&L!A13 (was 'Esc. %', now empty with its original style, as in the input); XML-level edit, every other cell unchanged. New golden scores 1.0 against itself.
- [F1](../findings.json) (Task Spec): Undisclosed requirement to populate header label 'Esc. %' in cell P&L!A13 causes all otherwise-correct solutions to score 0.0
  - Change: gt_18_RoadAssets_golden.xlsx: cleared the unrequested label at P&L!A13 (was 'Esc. %', now empty with its original style, as in the input); XML-level edit, every other cell unchanged. New golden scores 1.0 against itself.
- [F3](../findings.json) (Verification): Answer key requires an unrequested text label (P&L!A13 = 'Esc. %'), so a correct solution still scores 0
  - Change: gt_18_RoadAssets_golden.xlsx: cleared the unrequested label at P&L!A13 (was 'Esc. %', now empty with its original style, as in the input); XML-level edit, every other cell unchanged. New golden scores 1.0 against itself.
- [F2](../findings.json) (Task Spec): An unrequested text label is mandatory for receiving any credit
  - Change: gt_18_RoadAssets_golden.xlsx: cleared the unrequested label at P&L!A13 (was 'Esc. %', now empty with its original style, as in the input); XML-level edit, every other cell unchanged. New golden scores 1.0 against itself.
- other finding, major, not in findings.json: Price Index Multiple: 'escalate the prior year's value by the annual indexation rate' doesn't match the answer key, which compounds 1.02 every half-year column; the rate is also not an input anywhere
  - Change: problemStatement Revenue sentence: "... by escalating the prior year's value using the annual indexation rate." -> "... by escalating the prior period's value using the same indexation factor as the earlier columns." The key (S16:AF16 =prior column*1.02, as in E16:R16) is unchanged; the sheet has two (half-year) columns per FY and no annual-rate input, so the old wording described a different calculation.
