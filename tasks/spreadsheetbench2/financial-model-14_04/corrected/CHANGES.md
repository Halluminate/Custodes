# Changes: SpreadsheetBench 2 financial-model-14_04

Fix summary (from the fix record):

Replaced the golden NCD sheet's stale near-zero cached residuals with the values the verifier's LibreOffice recalculation produces, and dropped the 25 sensitivity-table cells K27:O31 from the graded range because LibreOffice cannot evaluate the TABLE() data table, so no correct sensitivity values can be keyed. The golden workbook now passes its own check (regression 1.0, modification 1.0).

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_14_Refinery_golden.xlsx

## Fixed

- [F6](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: gt_14_Refinery_golden.xlsx: 306 cached values on NCD (float residuals of about 1e-13, e.g. AA137 -3.375e-13 -> LibreOffice value) set to the verifier's LibreOffice recalculation, formulas and every other byte unchanged. Local verifier on the original golden and on the patched golden: PASS, reg 1.0, mod 1.0.
- [F2](../findings.json) (Reward): The golden workbook fails the sole verifier after mandatory recalculation
  - Change: Same NCD cached-value correction; the golden no longer fails on NCD residuals.
- [F7](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells trivially fails (score 0.0) on all runs and even on the ground-truth workbook itself
  - Change: NCD residual fix as above, plus answer_position 'DCF_Income Approach'!B1:O50 split into B1:O26, B27:J31 and B32:O50 so the 25 TABLE() cells K27:O31 (which LibreOffice reduces to the base-case 28810.17) are no longer compared.
- [F4](../findings.json) (Verification): Invalid golden solution and broken value comparison on DCF Sensitivity Analysis table, NCD, and TL sheets make the task unpassable
  - Change: Same two changes (NCD cached values, K27:O31 excluded from answer_position).
- [F1](../findings.json) (Verification): Ground-truth sensitivity table shows the same Equity Value in every WACC × terminal growth cell
  - Change: K27:O31 excluded from answer_position, so a working sensitivity table is no longer failed against the constant 28810.17 key.
- [F5](../findings.json) (Verification): The sensitivity-analysis answer key incorrectly expects a constant equity value
  - Change: Same K27:O31 exclusion.
- other finding, minor, not in findings.json: WC workings instruction names the wrong base year: the GT links 2021-22 to the 2020-21 column
  - Change: Prompt: "using 2021-22 as the base" -> "using 2020-21 as the base" (one word in the existing sentence), matching the golden H5 =G5, H11 =G11, H17 =G17. Answer key unchanged.

## Confirmed findings not fixed

- [F3](../findings.json): The EBITDA-margin answer key uses the wrong period for Q4
  - Reason: cannot-fix-safely: golden 'Profit & Loss'!J37 =K18/K6 follows the input's own convention for that column (J36 =K20/K6 and J38 =K30/K6 are already in the input), so switching the key to J18/J6 would fail agents that follow the model's existing row pattern.
