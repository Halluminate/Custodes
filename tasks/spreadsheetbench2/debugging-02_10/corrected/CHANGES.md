# Changes: SpreadsheetBench 2 debugging-02_10

Fix summary (from the fix record):

The answer key's first Berk-Hath sensitivity table (G11:K14) held corrupted values from a data table whose row headers depend on its own input cell. Those 20 cells now hold the values the model gives for their dividend and discount rates. Full pass: the key now also fixes the Synergies CVX column errors (Q11 price link, Q17 cash value, Q24 premium), and the #REF! cells Exhibit 9!N23:P23 are left out of grading.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_02_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: Verifier fails to evaluate data tables and compares Berk-Hath Investment Package!G11:K14 against corrupted ground-truth values
  - Change: gt_02_golden.xlsx, 'Berk-Hath Investment Package'!G11:K14 (20 hardcoded data-table results): replaced the corrupted values with the table's own model, PV(disc,10,-div*10000)+PV(disc,10,0,-10500)+736.33388 warrant, at dividend rates 7.5%/8%/8.5%/9% (F11:F14) and discount rates 6.3%-8.3% (G9:K9). Examples: G11 11152.88 -> 11878.54, I12 10429.31 -> 11468.40 (now equals the second table's I20), K14 10762.99 -> 11425.01. Row 10, which was already right, reproduces exactly under the same formula. No other cell changed. The patched GT scores 1.0 on the local SB2 cell check.
- [F1](../findings.json) (Verification): Broken ground truth and missing data-table evaluation in Berk-Hath Investment Package and DCF sensitivity tables
  - Change: Same GT fix to G11:K14. The other half of this finding (the verifier freezes TABLE() cells instead of evaluating them) is harness behaviour and is not changed here.
- [F3](../findings.json) (Verification): The answer key has wrong values in the Berk-Hath dividend-rate × discount-rate sensitivity table (G11:K14)
  - Change: Same GT fix to G11:K14.
- [F2](../findings.json) (Verification): Golden sensitivity table contains twenty incorrect required answers
  - Change: Same GT fix to G11:K14.
- other finding, major, not in findings.json: Undisclosed scope of graded fixes in open-ended audit prompt while other workbook defects are penalized as regressions
  - Change: gt_02_golden.xlsx (built on the critical-pass key), Synergies CVX column, XML-level edits: Q11 ='Exhibit 3'!$D$14 -> =+'Exhibit 8b'!$D$7 (65 -> 125.98999786377, the CVX price Merger Model!H14 uses); Q17 =Q11*Q15 -> =+Q15*Q16 (32779.5 -> 8194.875, mirrors D17); Q24 =Q17-Q22 -> =+Q19-Q22 (9178.26 -> 9176.01, mirrors D24); dependents Q12 12682.39 -> 24582.37 and Q19 45461.89 -> 32777.25 (now equal to Merger Model!I20's offer value). Nothing else references these cells. Exhibit 9!N23:P23 (#REF! in input and key, no single defensible repair) are left out of answer_position: 'Exhibit 9'!A1:P30 -> 'Exhibit 9'!A1:P22,'Exhibit 9'!A23:M23,'Exhibit 9'!A24:P30 (verifier parameter and the guidance's range list). SB2 scorer: new key 1.0; critical-pass key (planted fixes only) now 0.0 on Synergies Q11/Q12/Q17/Q19, as intended; untouched input 0.0 (214 cell errors). Prompt unchanged.
