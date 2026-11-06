# Changes: SpreadsheetBench 2 financial-model-14_02

Fix summary (from the fix record):

The answer key's float residue in untouched NCD/TL sheets failed even the GT, and its sensitivity grid was flat at the base value. Zeroed the residue, put true sensitivity values in K27:O31, and named the J26 corner cell in the prompt.

Changed files (in this folder):

- prompt.md
- reference/gt_14_Refinery_golden.xlsx

## Fixed

- [F8](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells is a trivial fail (cannot pass even on the ground-truth workbook itself)
  - Change: files/gt/gt_14_Refinery_golden.xlsx: set the cached value of 4,657 formula cells whose cached value was floating-point residue (0 < |v| < 1e-9; NCD 1,981, TL 2,674, Cash Flow F48/H48) to exactly 0. Formulas and every other cell unchanged. The verifier's 1% relative test then becomes an absolute 0.01 test on these cells, so recalculation noise no longer fails. Local check: patched GT scores PASS against itself after the verifier's forced LibreOffice recalc; plus the K27:O31 grid fix
- [F7](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: files/gt/gt_14_Refinery_golden.xlsx: set the cached value of 4,657 formula cells whose cached value was floating-point residue (0 < |v| < 1e-9; NCD 1,981, TL 2,674, Cash Flow F48/H48) to exactly 0. Formulas and every other cell unchanged. The verifier's 1% relative test then becomes an absolute 0.01 test on these cells, so recalculation noise no longer fails. Local check: patched GT scores PASS against itself after the verifier's forced LibreOffice recalc
- [F2](../findings.json) (Reward): Broken golden workbook and verifier comparison on floating-point zero residuals in untouched NCD and TL sheets
  - Change: files/gt/gt_14_Refinery_golden.xlsx: set the cached value of 4,657 formula cells whose cached value was floating-point residue (0 < |v| < 1e-9; NCD 1,981, TL 2,674, Cash Flow F48/H48) to exactly 0. Formulas and every other cell unchanged. The verifier's 1% relative test then becomes an absolute 0.01 test on these cells, so recalculation noise no longer fails. Local check: patched GT scores PASS against itself after the verifier's forced LibreOffice recalc
- [F3](../findings.json) (Verification): Golden Sensitivity Analysis table in DCF_Income Approach!K27:O31 contains constant base-case Equity Value in all 25 cells
  - Change: files/gt/gt_14_Refinery_golden.xlsx: replaced the 25 cached values of 'DCF_Income Approach'!K27:O31 (all 28810.17) with the true two-way sensitivity of Equity Value (D29) to terminal growth J27:J31 (into C18) and WACC K26:O26 (into C21), recomputed from the golden's own DCF rows (e.g. K27 28145.76, M29 25520.12, O31 23049.35; base case reproduces 28810.17). TABLE formulas kept
- [F1](../findings.json) (Task Spec): Undisclosed corner cell J26 requirement and strips of TABLE() formulas during recalculation
  - Change: prompt.md: the DCF sentence now says the table links Equity Value 'via the table's corner cell J26', disclosing the GT's J26 =D29. Together with the grid fix, explicit grid formulas plus J26 pass (local check: input + GT formulas + explicit grid values scores mod 1.0, reg 1.0 outside 'Amortization with extra payment', which fails locally even on the raw input under LibreOffice 26.8 but not in prod runs). The verifier stripping TABLE() formulas before recalculation is harness behaviour and is not changed
- [F6](../findings.json) (Reward): Floating-point noise (~1e-13) in TL/NCD cells counts as modification errors under relative tolerance, so the ground truth and correct solutions fail the binary grader
  - Change: files/gt/gt_14_Refinery_golden.xlsx: set the cached value of 4,657 formula cells whose cached value was floating-point residue (0 < |v| < 1e-9; NCD 1,981, TL 2,674, Cash Flow F48/H48) to exactly 0. Formulas and every other cell unchanged. The verifier's 1% relative test then becomes an absolute 0.01 test on these cells, so recalculation noise no longer fails. Local check: patched GT scores PASS against itself after the verifier's forced LibreOffice recalc
- [F4](../findings.json) (Verification): GT sensitivity table is flat: all 25 cells equal the base Equity Value, so a correct sensitivity grid fails
  - Change: files/gt/gt_14_Refinery_golden.xlsx: replaced the 25 cached values of 'DCF_Income Approach'!K27:O31 (all 28810.17) with the true two-way sensitivity of Equity Value (D29) to terminal growth J27:J31 (into C18) and WACC K26:O26 (into C21), recomputed from the golden's own DCF rows (e.g. K27 28145.76, M29 25520.12, O31 23049.35; base case reproduces 28810.17). TABLE formulas kept
- other finding, major, not in findings.json: Ambiguity in Cash and Cash Equivalents definition on DCF_Income Approach!D28
  - Change: problemStatement: the Equity Value clause now says to count cash, other bank balances and investments from the Balance sheet as cash, matching the key's D28 ='Balance sheet'!I25+I26+I14+I23 (and the model's own CFS cash check SUM(I25:I26)). One changed sentence.

## Confirmed findings not fixed

- [F5](../findings.json): The sensitivity-analysis answer key contains the same base-case value in every scenario
  - Reason: duplicate-of:F4
