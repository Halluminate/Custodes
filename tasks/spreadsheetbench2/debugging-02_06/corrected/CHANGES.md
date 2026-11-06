# Changes: SpreadsheetBench 2 debugging-02_06

Fix summary (from the fix record):

Removed the 100 what-if data-table grid cells (DCF!V10:Z14 and Berk-Hath Investment Package G10:K14, G18:K22, G26:K30) from the cell check's answer_position. The grader's LibreOffice recalculation cannot reproduce these cells, and the answer key's Berk-Hath values are wrong. Everything else is graded as before. Full pass: the key also fixes the Synergies CVX column (Q11 price link, Q17 cash value, Q24 premium); Exhibit 9!N23:P23 (#REF!) and the Merger Model net-gain blocks, which have no single repair, are left out of grading.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_02_golden.xlsx

## Fixed

- [F5](../findings.json) (Verification): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells produces false negatives (score 0.0 on all units) due to corrupted sensitivity table values in gt_02_golden.xlsx vs untouched_input
  - Change: verifications[0].parameters.answer_position: the 'DCF'!B1:Z35 range and the 'Berk-Hath Investment Package'!B2:K44 range are split so they skip the data-table grids DCF!V10:Z14, Berk-Hath G10:K14, G18:K22 and G26:K30 (TABLE() cells in the input). All other ranges are unchanged. Checked locally with the unchanged golden: the 5 intended fixes applied to the input with openpyxl now score 1.0 (they scored 0 before), the golden scores 1.0 and the untouched input scores 0.
- [F2](../findings.json) (Verification): Invalid golden solution and corrupted input data-table values in 'Berk-Hath Investment Package'!G10:K14 make 22 of 91 modification cells impossible to pass properly
  - Change: The 22 Berk-Hath G10:K14 modification cells (corrupted golden values vs frozen 11432.17 input caches) are no longer graded, via the same answer_position change.
- [F3](../findings.json) (Verification): The answer key's Berk-Hath sensitivity table (rows 11-14) is wrong, so a correct agent cannot pass
  - Change: The wrong golden Berk-Hath rows 11-14 are no longer compared (answer_position excludes G10:K14), so a correct sensitivity table is not penalised.
- [F1](../findings.json) (Reward): Leaving the data-table formulas as they are fails the grader: they come out blank after its LibreOffice recalc, so the agent must hardcode 100 cells
  - Change: All TABLE() grid cells, which come out blank or frozen after the grader's recalculation, are excluded from answer_position, so leaving them as formulas no longer fails.
- [F4](../findings.json) (Verification): Golden sensitivity-table values contradict the model and reject correct calculations
  - Change: Same answer_position change: the contradictory golden sensitivity values are no longer graded.
- other finding, major, not in findings.json: Open-ended audit prompt instructs agent to fix all formula logic and broken reference errors, but golden file only fixes 5 cross-sheet references and penalizes fixing other genuine bugs in graded ranges
  - Change: gt_02_golden.xlsx, Synergies CVX column, XML formula edits: Q11 ='Exhibit 3'!$D$14 -> =+'Exhibit 8b'!$D$7 (65 -> 125.99, the CVX price Merger Model!H14 uses); Q17 =Q11*Q15 -> =+Q15*Q16 (32779.5 -> 8194.875, mirrors D17); Q24 =Q17-Q22 -> =+Q19-Q22 (mirrors D24); caches of Q11, Q12, Q17, Q19, Q24 set from the SB2 LibreOffice recalc, nothing else changed. answer_position (and graderGuidance range list): Exhibit 9!N23:P23 (#REF!, no single repair) and the Merger Model net-gain blocks C29:E32 and C57:E60 (cash consideration added to APC's gain but never deducted from NewCo/OXY; several valid repairs) are left out: 'Merger Model'!B2:J85 -> B2:J28,B29:B32,F29:J32,B33:J56,B57:B60,F57:J60,B61:J85 and 'Exhibit 9'!A1:P30 -> A1:P22,A23:M23,A24:P30. Real scorer: new key 1.0; untouched input + 5 planted + 3 Synergies fixes 1.0; same plus a cash-deducting E29/E57 repair 1.0; untouched input 0.0; the previous key now fails only on Synergies Q11/Q12/Q17/Q19.
