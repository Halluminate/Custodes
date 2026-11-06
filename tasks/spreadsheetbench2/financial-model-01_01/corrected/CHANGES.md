# Changes: SpreadsheetBench 2 financial-model-01_01

Fix summary (from the fix record):

The answer key used the 2% Key Assumption for forecast Other Revenue %, but the prompt says to hardcode the last actual year's value (0.1537%). The key now hardcodes 0.1537% in Revenue Drivers!I138 and all dependent cached values are recomputed.

Changed files (in this folder):

- reference/gt_01_Education_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: Verifier fails all three valid agent submissions (false negative) due to contradictory ground-truth assumption in Revenue Drivers!I138:M138
  - Change: gt_01_Education_golden.xlsx: 'Revenue Drivers'!I138 changed from ='Key Assumptions'!D9 (2%) to the hardcoded last-actual-year value 0.00153691620609951 (= H138, 4.8948374/3184.843377). J138:M138 keep their =I138 chain. Cached values were recomputed in LibreOffice: 424 dependent cells changed (Revenue Drivers 137/138, Consolidated P&L, BS, CF, Ratio Analysis, Working Capital, Forecast, DCF), no formulas or formats changed. DCF Valuation!C22 is now 2238.42836435011, matching the three runs that followed the prompt.
- [F1](../findings.json) (Task Spec): Task instruction for forecasted Other Revenue % of Operating Revenue directly contradicts the ground-truth workbook
  - Change: gt_01_Education_golden.xlsx: 'Revenue Drivers'!I138 changed from ='Key Assumptions'!D9 (2%) to the hardcoded last-actual-year value 0.00153691620609951 (= H138, 4.8948374/3184.843377). J138:M138 keep their =I138 chain. Cached values were recomputed in LibreOffice: 424 dependent cells changed (Revenue Drivers 137/138, Consolidated P&L, BS, CF, Ratio Analysis, Working Capital, Forecast, DCF), no formulas or formats changed. DCF Valuation!C22 is now 2238.42836435011, matching the three runs that followed the prompt.
- [F2](../findings.json) (Verification): The instruction says to carry forward the last actual year's Other Revenue %, but the answer key uses the 2% Key Assumption
  - Change: gt_01_Education_golden.xlsx: 'Revenue Drivers'!I138 changed from ='Key Assumptions'!D9 (2%) to the hardcoded last-actual-year value 0.00153691620609951 (= H138, 4.8948374/3184.843377). J138:M138 keep their =I138 chain. Cached values were recomputed in LibreOffice: 424 dependent cells changed (Revenue Drivers 137/138, Consolidated P&L, BS, CF, Ratio Analysis, Working Capital, Forecast, DCF), no formulas or formats changed. DCF Valuation!C22 is now 2238.42836435011, matching the three runs that followed the prompt.
- [F3](../findings.json) (Verification): Ground truth contradicts the required Other Revenue forecast assumption
  - Change: gt_01_Education_golden.xlsx: 'Revenue Drivers'!I138 changed from ='Key Assumptions'!D9 (2%) to the hardcoded last-actual-year value 0.00153691620609951 (= H138, 4.8948374/3184.843377). J138:M138 keep their =I138 chain. Cached values were recomputed in LibreOffice: 424 dependent cells changed (Revenue Drivers 137/138, Consolidated P&L, BS, CF, Ratio Analysis, Working Capital, Forecast, DCF), no formulas or formats changed. DCF Valuation!C22 is now 2238.42836435011, matching the three runs that followed the prompt.
