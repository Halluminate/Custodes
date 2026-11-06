# Changes: SpreadsheetBench 2 financial-model-14_05

Fix summary (from the fix record):

Float residue (~1e-13) in the answer key's untouched NCD/TL cells made even the GT fail the all-or-nothing cell check. Set those residues to exactly 0 in the GT so they compare on the absolute 0.01 tolerance.

Changed files (in this folder):

- reference/gt_14_Refinery_golden.xlsx

## Fixed

- [F5](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells trivially fails (score 0.0) on all 3 units despite every unit producing the exact ground-truth formulas
  - Change: files/gt/gt_14_Refinery_golden.xlsx: set the cached value of 4,657 formula cells whose cached value was floating-point residue (0 < |v| < 1e-9; NCD 1,981, TL 2,674, Cash Flow F48/H48) to exactly 0. Formulas and every other cell unchanged. The verifier's 1% relative test then becomes an absolute 0.01 test on these cells, so recalculation noise no longer fails. Local check: patched GT scores PASS against itself after the verifier's forced LibreOffice recalc
- [F4](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: files/gt/gt_14_Refinery_golden.xlsx: set the cached value of 4,657 formula cells whose cached value was floating-point residue (0 < |v| < 1e-9; NCD 1,981, TL 2,674, Cash Flow F48/H48) to exactly 0. Formulas and every other cell unchanged. The verifier's 1% relative test then becomes an absolute 0.01 test on these cells, so recalculation noise no longer fails. Local check: patched GT scores PASS against itself after the verifier's forced LibreOffice recalc
- [F3](../findings.json) (Reward): Verifier grades untouched floating-point zero-residuals (~1e-13) in NCD and TL using relative tolerance before rounding, causing even the golden workbook to fail
  - Change: files/gt/gt_14_Refinery_golden.xlsx: set the cached value of 4,657 formula cells whose cached value was floating-point residue (0 < |v| < 1e-9; NCD 1,981, TL 2,674, Cash Flow F48/H48) to exactly 0. Formulas and every other cell unchanged. The verifier's 1% relative test then becomes an absolute 0.01 test on these cells, so recalculation noise no longer fails. Local check: patched GT scores PASS against itself after the verifier's forced LibreOffice recalc
- [F2](../findings.json) (Reward): Graded answer range covers untouched sheets, so float/recalculation noise (e.g., NCD balance rows) is graded as modification and the ground truth fails its own verifier
  - Change: files/gt/gt_14_Refinery_golden.xlsx: set the cached value of 4,657 formula cells whose cached value was floating-point residue (0 < |v| < 1e-9; NCD 1,981, TL 2,674, Cash Flow F48/H48) to exactly 0. Formulas and every other cell unchanged. The verifier's 1% relative test then becomes an absolute 0.01 test on these cells, so recalculation noise no longer fails. Local check: patched GT scores PASS against itself after the verifier's forced LibreOffice recalc

## Confirmed findings not fixed

- [F1](../findings.json): The golden workbook fails its own verifier after mandatory recalculation
  - Reason: duplicate-of:F3
