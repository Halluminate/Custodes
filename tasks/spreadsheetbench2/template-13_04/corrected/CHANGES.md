# Changes: SpreadsheetBench 2 template-13_04

Fix summary (from the fix record):

The answer key had deleted the seeded 2022 tax-rate input E36 = 0.35, so agents that kept it (as told) failed. I restored E36 in the golden workbook.

Changed files (in this folder):

- reference/gt_13_04_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells gives false-negative 0.0 score across all 3 units due to missing E36 value in golden workbook
  - Change: gt_13_04_golden.xlsx: restored the seeded input Normalize_Adjustments!E36 = 0.35 (2022 effective tax rate on adjustments), which the golden had blanked; nothing references it, no other cell changed.
- [F2](../findings.json) (Verification): Corrupted ground-truth cell E36 in gt_13_04_golden.xlsx contradicts task instructions and causes valid solutions to fail
  - Change: gt_13_04_golden.xlsx: restored the seeded input Normalize_Adjustments!E36 = 0.35 (2022 effective tax rate on adjustments), which the golden had blanked; nothing references it, no other cell changed.

## Confirmed findings not fixed

- [F1](../findings.json): The answer key deletes the seeded input value E36, so an agent that follows the 'don't alter existing cells' rule fails the only verifier
  - Reason: duplicate-of:F2
- [F3](../findings.json): Answer key requires deleting a supplied tax assumption, contradicting preservation instructions
  - Reason: duplicate-of:F2
