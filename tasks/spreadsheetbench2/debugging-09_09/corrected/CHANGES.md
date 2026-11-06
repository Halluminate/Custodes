# Changes: SpreadsheetBench 2 debugging-09_09

Fix summary (from the fix record):

The circular revolver/interest block on LBO (289 cells that LibreOffice does not settle in one recalc) is left out of the graded range, so the original key passes its own check and outputs saved with or without caches grade the same; key unchanged.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F4](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: verifications[0].parameters.answer_position: left out the 289 LBO cells of the circular revolver/interest loop that do not settle under one LibreOffice recalc (G:N block of rows 67-205 and LBO!D213/L213; found by scoring the re-cached key, the original key and the key with no caches against the key). graderGuidance range list updated to match. Answer key unchanged. Real scorer: original key vs itself PASS 1.0/1.0 (was 0.0), key with no caches PASS, untouched input FAIL (mod 0.0).
- [F5](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells is a trivial fail (0.0) because LibreOffice recalculation diverges from un-converged cached values in gt_09_golden.xlsx
  - Change: Same answer_position carve-out of the non-settling circular loop cells (see gt-replay-0); the key now passes its own check.
- [F1](../findings.json) (Reward): Golden workbook (gt_09_golden.xlsx) contains un-converged circular-reference cached values and fails its own verifier check
  - Change: Same answer_position carve-out of the non-settling circular loop cells (see gt-replay-0); the key now passes its own check.
- [F2](../findings.json) (Reward): Ground-truth workbook fails its own verifier: its cached circular-model values never converged
  - Change: Same answer_position carve-out of the non-settling circular loop cells (see gt-replay-0); the key now passes its own check.
- [F3](../findings.json) (Reward): Inconsistent golden-workbook caches cause the answer key to fail its own verifier
  - Change: Same answer_position carve-out of the non-settling circular loop cells (see gt-replay-0); the key now passes its own check.
