# Changes: SpreadsheetBench 2 debugging-07_01

Fix summary (from the fix record):

Replaced the answer key (and reference) with fully converged circular-block values so the golden passes its own check. Full pass: the key also fixes the Equity Returns I57 preference-return formula QA named. Cleanup pass: the 30 loop cells that do not settle under one LibreOffice recalc are left out of answer_position, so an output saved without cached values also passes.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_07_golden.xlsx
- reference/untouched_input_Double Counting_input.xlsx

## Fixed

- [F4](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: Replaced gt_07_golden.xlsx and the reference workbook with copies recalculated through the verifier's LibreOffice path repeatedly (8 passes) until the circular interest/debt block in LBO & Lenders converged; the converged values match the closed-form fixed point (e.g. T50 -7.244, X50 -12.072, formulas unchanged). The new golden scores 1.0 against itself, and so does a workbook whose caches are one LibreOffice pass from converged. Residual risk (infra): an output saved with no cached values (e.g. plain openpyxl) still does not converge in the verifier's single LibreOffice pass.
- [F5](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells fails correct solutions (score 0.0 on units 1 and 2, and on the golden file itself) because it force-recalculates output_path but compares against unconverged cached values in gt_07_golden.xlsx
  - Change: Replaced gt_07_golden.xlsx and the reference workbook with copies recalculated through the verifier's LibreOffice path repeatedly (8 passes) until the circular interest/debt block in LBO & Lenders converged; the converged values match the closed-form fixed point (e.g. T50 -7.244, X50 -12.072, formulas unchanged). The new golden scores 1.0 against itself, and so does a workbook whose caches are one LibreOffice pass from converged. Residual risk (infra): an output saved with no cached values (e.g. plain openpyxl) still does not converge in the verifier's single LibreOffice pass.
- [F1](../findings.json) (Reward): Unconverged circular-reference cached values in gt_07_golden.xlsx and un-recalculated GT comparison make the task impossible to pass
  - Change: Replaced gt_07_golden.xlsx and the reference workbook with copies recalculated through the verifier's LibreOffice path repeatedly (8 passes) until the circular interest/debt block in LBO & Lenders converged; the converged values match the closed-form fixed point (e.g. T50 -7.244, X50 -12.072, formulas unchanged). The new golden scores 1.0 against itself, and so does a workbook whose caches are one LibreOffice pass from converged. Residual risk (infra): an output saved with no cached values (e.g. plain openpyxl) still does not converge in the verifier's single LibreOffice pass.
- [F2](../findings.json) (Reward): GT cached LBO interest/debt values in the circular block are not converged, so the golden workbook fails its own grader after LibreOffice recalculation and is internally inconsistent
  - Change: Replaced gt_07_golden.xlsx and the reference workbook with copies recalculated through the verifier's LibreOffice path repeatedly (8 passes) until the circular interest/debt block in LBO & Lenders converged; the converged values match the closed-form fixed point (e.g. T50 -7.244, X50 -12.072, formulas unchanged). The new golden scores 1.0 against itself, and so does a workbook whose caches are one LibreOffice pass from converged. Residual risk (infra): an output saved with no cached values (e.g. plain openpyxl) still does not converge in the verifier's single LibreOffice pass.
- [F3](../findings.json) (Reward): The golden workbook fails its own verifier after mandatory recalculation
  - Change: Replaced gt_07_golden.xlsx and the reference workbook with copies recalculated through the verifier's LibreOffice path repeatedly (8 passes) until the circular interest/debt block in LBO & Lenders converged; the converged values match the closed-form fixed point (e.g. T50 -7.244, X50 -12.072, formulas unchanged). The new golden scores 1.0 against itself, and so does a workbook whose caches are one LibreOffice pass from converged. Residual risk (infra): an output saved with no cached values (e.g. plain openpyxl) still does not converge in the verifier's single LibreOffice pass.
- other finding, major, not in findings.json: The answer key penalizes a valid correction explicitly required by the comprehensive audit
  - Change: gt_07_golden.xlsx (built on the prepared converged golden): 'Equity Returns'!I57 '=I56*(1+$D$12)^$D$10-1' -> '=I56*(1+$D$12)^$D$10-I56' at XML level; 17 dependent cached values on Equity Returns (I57 -210962.97, I58, I60 775675.95, H68:I70, H83:I86) taken from the verifier's LibreOffice recalc, everything else byte-identical. No other sheet references Equity Returns. answer_position unchanged (I57 is inside 'Equity Returns'!A2:I122). Real SB2 scorer: new key vs itself PASS 1.0/1.0; untouched input plus the key's 17 formula fixes PASS 1.0/1.0; same without the I57 fix FAIL (mod 0.81); untouched input FAIL (mod 0.0).
