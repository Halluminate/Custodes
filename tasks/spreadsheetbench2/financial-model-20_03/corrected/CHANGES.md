# Changes: SpreadsheetBench 2 financial-model-20_03

Fix summary (from the fix record):

The golden workbook cached floating-point residue (-4.95e-10) in the Cashflow!E31 balance check, which the relative tolerance rejects against LibreOffice's own residue. The cached value is now 0 (formula unchanged), so the absolute tolerance applies and the golden and correct outputs pass.

Changed files (in this folder):

- reference/gt_20_Fintech_golden.xlsx

## Fixed

- [F4](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: gt_20_Fintech_golden.xlsx Cashflow!E31: cached value -4.94765117764473e-10 set to 0, formula =E29-'Balance Sheet'!E9 kept, no other cell changed. Local grade: golden 1.0/1.0, simulated output with E31=-5.2387e-10 now passes (was mod 0.9993).
- [F5](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells fails all 3 correct runs (and fails the golden workbook itself) due to floating-point residue at Cashflow!E31
  - Change: Same GT edit (Cashflow!E31 cached 0), which removes the only failing cell in all 3 trial grades.
- [F2](../findings.json) (Reward): Cashflow!E31 in golden workbook holds floating-point residue (-4.95e-10) instead of 0, causing relative-tolerance check to fail on LibreOffice-recalculated outputs
  - Change: Same GT edit (Cashflow!E31 cached 0).
- [F1](../findings.json) (Reward): The ground-truth workbook fails its own verifier because of floating-point noise in a balance check cell
  - Change: Same GT edit (Cashflow!E31 cached 0).
- [F3](../findings.json) (Reward): Verifier rejects its own golden workbook because of floating-point noise
  - Change: Same GT edit (Cashflow!E31 cached 0).
