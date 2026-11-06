# Changes: SpreadsheetBench 2 financial-model-01_02

Fix summary (from the fix record):

The answer key added an unrequested header date in Working Capital Schedule!M3, which an agent following the instructions would not add. Removed it from the GT (no formula refers to it).

Changed files (in this folder):

- reference/gt_01_Education_golden.xlsx

## Fixed

- [F1](../findings.json) (Verification): Ground truth expects an unrequested edit to Working Capital Schedule!M3, so an agent that does exactly what was asked scores 0
  - Change: files/gt/gt_01_Education_golden.xlsx: cleared 'Working Capital Schedule'!M3 (was '=EOMONTH(L3,12)'; style kept, column M otherwise empty and unreferenced), matching the input. Local check: patched GT and input+requested GT edits both PASS
