# Changes: SpreadsheetBench 2 financial-model-07_03

Fix summary (from the fix record):

The golden and reference workbooks held stale #NAME? XLOOKUP caches, so the GT failed its own recalculating check, and the golden EQx used row 66 while the prompt names Net Cashflows After Financing (row 74). Both files were recalculated and the golden EQx formula now uses row 74.

Changed files (in this folder):

- reference/gt_07_RealEstate_golden.xlsx
- reference/untouched_input_07_03_RealEstate_input.xlsx

## Fixed

- [F5](../findings.json) (Verification): Golden gate: the ground-truth deliverable does not score full reward
  - Change: Replaced gt_07_RealEstate_golden.xlsx and untouched_input_07_03_RealEstate_input.xlsx with copies recalculated in LibreOffice through the verifier's own recalc pipeline, so the cached #NAME? XLOOKUP results in Sales Schedule!D18:D102 and every downstream zero are replaced by real values (1,349 cached values change in the GT, formulas unchanged apart from D80 below). Local grade: the GT formulas as output now pass (reg 1.0, mod 1.0), untouched input fails.
- [F6](../findings.json) (Verification): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check trivially fails all runs (including exact golden solutions) because it recalculates only output.xlsx while comparing against stale #NAME? cached values in gt_path and reference_path
  - Change: Replaced gt_07_RealEstate_golden.xlsx and untouched_input_07_03_RealEstate_input.xlsx with copies recalculated in LibreOffice through the verifier's own recalc pipeline, so the cached #NAME? XLOOKUP results in Sales Schedule!D18:D102 and every downstream zero are replaced by real values (1,349 cached values change in the GT, formulas unchanged apart from D80 below). Local grade: the GT formulas as output now pass (reg 1.0, mod 1.0), untouched input fails.
- [F1](../findings.json) (Verification): Ground-truth workbook has stale #NAME? cached values from un-evaluated _xlfn.xlookup formulas and fails its own verifier after LibreOffice recalculation
  - Change: Replaced gt_07_RealEstate_golden.xlsx and untouched_input_07_03_RealEstate_input.xlsx with copies recalculated in LibreOffice through the verifier's own recalc pipeline, so the cached #NAME? XLOOKUP results in Sales Schedule!D18:D102 and every downstream zero are replaced by real values (1,349 cached values change in the GT, formulas unchanged apart from D80 below). Local grade: the GT formulas as output now pass (reg 1.0, mod 1.0), untouched input fails.
- [F2](../findings.json) (Verification): The golden workbook fails its own verifier after recalculation
  - Change: Replaced gt_07_RealEstate_golden.xlsx and untouched_input_07_03_RealEstate_input.xlsx with copies recalculated in LibreOffice through the verifier's own recalc pipeline, so the cached #NAME? XLOOKUP results in Sales Schedule!D18:D102 and every downstream zero are replaced by real values (1,349 cached values change in the GT, formulas unchanged apart from D80 below). Local grade: the GT formulas as output now pass (reg 1.0, mod 1.0), untouched input fails.
- [F4](../findings.json) (Task Spec): Prompt instruction for Project Performance EQx specifies 'Net Cashflows After Financing' (row 74) but ground truth uses 'Net Cashflows' before financing (row 66)
  - Change: Answer key fixed to match the instruction: gt_07_RealEstate_golden.xlsx 'Cashflow (Monthly)'!D80 changed from =SUMIF(J66:BG66,">0")/-SUMIF(J66:BG66,"<0") (Net Cashflows) to =SUMIF(J74:BG74,">0")/-SUMIF(J74:BG74,"<0") (row 74, Net Cashflows After Financing), recalculated: D80 and 'Cashflow (Quaterly)'!D80 now 1.379244 instead of 1.552119.
- [F3](../findings.json) (Verification): The expected EQx formula uses cashflows before financing
  - Change: Answer key fixed to match the instruction: gt_07_RealEstate_golden.xlsx 'Cashflow (Monthly)'!D80 changed from =SUMIF(J66:BG66,">0")/-SUMIF(J66:BG66,"<0") (Net Cashflows) to =SUMIF(J74:BG74,">0")/-SUMIF(J74:BG74,"<0") (row 74, Net Cashflows After Financing), recalculated: D80 and 'Cashflow (Quaterly)'!D80 now 1.379244 instead of 1.552119.
