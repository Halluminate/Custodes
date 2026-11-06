# Changes: SpreadsheetBench 2 template-06_24

Fix summary (from the fix record):

FY-column cells the key leaves blank (store counts and FY sums an analyst may fill) are no longer graded, so completing them is not penalized.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: The FY 2023 column is filled in only some rows, so an agent that completes the other FY cells fails on cells the key leaves blank
  - Change: verifications[0].parameters.answer_position: 'RevenueBuild'!B2:G37 now leaves out the FY 2023 cells that the key leaves blank but an analyst may reasonably fill (G11:G14, G16:G17, G21:G24, G35, G37). The graded FY cells G29, G30, G32 and G36 and all quarterly cells stay graded. The grader guidance range is updated to match. Checked with the real SB2 scorer: golden 1.0, input plus the key's changes 1.0, golden plus filled FY cells (G35=C35, G37=F37, FY sums/averages) 1.0 (under the old range every such cell was a regression mismatch, and one mismatch in 216 cells is below the 0.998 bar), untouched input 0.0.
