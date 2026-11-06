# Changes: SpreadsheetBench 2 template-11_03

Fix summary (from the fix record):

The answer key deleted the existing 'Starting Rate:' label in MergerPremium!F35, so agents that preserved it, as instructed, failed. Restored the label in the GT.

Changed files (in this folder):

- reference/gt_11_03_golden.xlsx

## Fixed

- [F2](../findings.json) (Verification): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells enforces an erroneous deletion of pre-existing input cell MergerPremium!F35
  - Change: files/gt/gt_11_03_golden.xlsx: restored 'MergerPremium'!F35 = 'Starting Rate:' (the input's label, which the GT had cleared). Nothing else changed. F35 is now a regression cell, so keeping the label passes. Local check: patched GT and input+GT edits both PASS
- [F1](../findings.json) (Verification): Ground truth deletes pre-existing input label in F35 ('Starting Rate:'), causing compliant agents to fail
  - Change: files/gt/gt_11_03_golden.xlsx: restored 'MergerPremium'!F35 = 'Starting Rate:' (the input's label, which the GT had cleared). Nothing else changed. F35 is now a regression cell, so keeping the label passes. Local check: patched GT and input+GT edits both PASS
