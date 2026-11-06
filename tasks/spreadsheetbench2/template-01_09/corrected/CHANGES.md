# Changes: SpreadsheetBench 2 template-01_09

Fix summary (from the fix record):

The answer key's year-4 tax side did not reconcile: the tax gain on extinguishment was never booked, so deferred taxes and cash taxes were wrong and the tax loan kept a 1,200 balance. The gain is now booked in F36 and the GT is reconciled. The two pre-filled zeros the key must overwrite (F32, F36) are cleared in the input.

Changed files (in this folder):

- reference/gt_01_09_golden.xlsx
- reference/untouched_input_01_09_input.xlsx
- inputs/01_09_input.xlsx

## Fixed

- [F6](../findings.json) (Verification): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells scores 0.0 on all runs by rejecting accounting-consistent Year 4 tax and interest calculations against a flawed ground truth
  - Change: gt_01_09_golden.xlsx BondAccounting year 4: F36 (tax-book gain on extinguishment) =F31+K6 = 1,200, which the GT's own F12 formula =-F7*F13-F36*F13 already expects. F12 therefore becomes -308.90, matching F25 =-E26. F11 =F10-F12 = 2,380, above GAAP tax 2,071.10 as note J11 says. F32 =-F31 = -31,200, so F33 = 0 and F37 = 1,200. A forced LibreOffice recalculation of the patched GT reproduces every cached value, and it scores reg 1.0 / mod 1.0 locally. Input BondAccounting!F32 and F36 (pre-filled 0) are now blank in 01_09_input.xlsx and untouched_input_01_09_input.xlsx. They are year-4 cells the answer key fills, so the 'do not alter pre-filled cells' rule no longer blocks the correct answer.
- [F3](../findings.json) (Verification): Golden workbook (gt_01_09_golden.xlsx) contains broken Year 4 tax formulas and overwrites pre-filled cell F32, contradicting in-sheet note J11 and prompt rules
  - Change: GT F12 = -308.90, F11 = 2,380 (consistent with J11). Input F32/F36 blanked so overwriting them no longer breaks the no-alter rule.
- [F5](../findings.json) (Verification): The answer key's year-4 deferred-tax logic is internally inconsistent and contradicts the workbook's own note
  - Change: GT F36 = 1,200 gain, so F12 = -308.90 = F25 and F11 = 2,380 > F10, as J11 says.
- [F2](../findings.json) (Verification): Tax balance sheet in the answer key leaves a 1,200 loan balance after the debt is extinguished, and books no gain or loss
  - Change: GT F32 =-F31 (-31,200) retires the full tax basis, F33 = 0, and the 1,200 gain is booked in F36/F37. Row 29 (=C25) is left unchanged. The core defect (a tax balance that is never retired and no gain booked) is fixed.
- [F1](../findings.json) (Verification): Passing requires changing a prefilled cell protected by the instructions
  - Change: Input BondAccounting!F32 and F36 (pre-filled 0) are now blank in 01_09_input.xlsx and untouched_input_01_09_input.xlsx. They are year-4 cells the answer key fills, so the 'do not alter pre-filled cells' rule no longer blocks the correct answer.
- [F4](../findings.json) (Verification): Year-4 tax answer key does not reconcile
  - Change: Year 4 now reconciles: F10 2,071.10 = F11 2,380 + (F25 - F21) -308.90.
