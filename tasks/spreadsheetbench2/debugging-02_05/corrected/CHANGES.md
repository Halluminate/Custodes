# Changes: SpreadsheetBench 2 debugging-02_05

Fix summary (from the fix record):

The cell check no longer grades the Berk-Hath sensitivity grid G10:K14, whose golden values are corrupted and cannot be reproduced, so a correct AVERAGE fix now passes.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check fails all units (score 0.0) including exact fixes of all intended AVERAGE bugs due to corrupted golden Data Table values
  - Change: verifications[0].answer_position: 'Berk-Hath Investment Package'!B2:K44 split into B2:K9, B10:F14, B15:K44, dropping the dividend-rate x discount-rate data-table grid G10:K14, whose golden values are corrupted (rows 11=12 and 10=13). graderGuidance range text updated to match. Checked locally with the verifier code: input + the three golden AVERAGE fixes (DCF!I15, WACC!D7, WACC!D14) now scores reg 1.0 / mod 1.0 (was mod 0.15 with 22 G10:K14 errors); the golden scores 1.0; the unchanged input still fails.
- [F1](../findings.json) (Verification): Corrupted ground truth values in Berk-Hath Investment Package!G10:K14 make the sole verifier impossible to pass
  - Change: Same answer_position change (G10:K14 excluded).
- [F2](../findings.json) (Verification): Answer key for the Berk-Hath dividend-rate × discount-rate sensitivity table (G10:K14) is wrong, so a correct fix can never pass the binary verifier
  - Change: Same answer_position change (G10:K14 excluded).
- [F3](../findings.json) (Verification): Incorrect golden sensitivity values make a correct audit fail
  - Change: Same answer_position change (G10:K14 excluded).
