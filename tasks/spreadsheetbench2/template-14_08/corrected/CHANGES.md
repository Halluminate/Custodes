# Changes: SpreadsheetBench 2 template-14_08

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, major, not in findings.json: No stated rule for whether capital reserves grow over 5 years; the ground truth keeps them flat and a binary verifier rejects inflating them
  - Change: Prompt: added one sentence after the instruction, "Keep capital reserves flat at the per-unit annual amount in every year." (the key's C64:G64 =$C$17*$C$7 and C45:F45 =$C$17*$C$7/4). Answer key unchanged.
