# Changes: SpreadsheetBench 2 financial-model-04_03

Fix summary (from the fix record):

The answer key's Debt / Equity row divided debt by Total Assets (Financials row 87). It now divides by Total Equity (Financials row 103), and the Final Output cells that link to it carry the new values. Full pass: the prompt now asks to complete the Valuation Blended Price section, whose cells were graded but never requested.

Changed files (in this folder):

- prompt.md
- reference/gt_04_Consumer_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: Verifier fails all units due to flawed ground-truth formula for Debt/Equity (dividing by Total Assets instead of Total Equity)
  - Change: gt_04_Consumer_golden.xlsx 'Ratio_Analysis '!F25:O25 changed from =+(Financials!X95+Financials!X90)/Financials!X87 to =+(Financials!X95+Financials!X90)/Financials!X103, with cached values recomputed (F25 0.274 -> 0.583 ... O25 0.192 -> 0.350). 'Final Output'!L37:Q37 (links to J25:O25) get the matching cached values. Nothing else changed. The patched GT, recalculated in LibreOffice, scores reg 1.0 / mod 1.0 locally.
- [F3](../findings.json) (Verification): Ground truth for 'Debt / Equity' in Ratio_Analysis divides by Total Assets instead of Total Equity
  - Change: Same GT fix: 'Ratio_Analysis '!F25:O25 denominator now Financials row 103 (Total Equity), and Final Output L37:Q37 caches updated.
- [F2](../findings.json) (Verification): The answer key computes Debt/Equity as debt divided by Total Assets, not by Equity
  - Change: Same GT fix: 'Ratio_Analysis '!F25:O25 denominator now Financials row 103 (Total Equity), and Final Output L37:Q37 caches updated.
- [F1](../findings.json) (Verification): Debt/Equity answer key divides debt by assets instead of equity
  - Change: Same GT fix: 'Ratio_Analysis '!F25:O25 denominator now Financials row 103 (Total Equity), and Final Output L37:Q37 caches updated.
- other finding, major, not in findings.json: Undisclosed requirement to populate Blended Price table (Valuation!D95, G95, D97, G97, D99, G99)
  - Change: Prompt sentence 'In the Valuation sheet, calculate WACC.' changed to 'In the Valuation sheet, calculate WACC and complete the Blended Price section.' The graded Blended Price cells (D95, G95, D97, G97, D99, G99) are now requested. Key and verifier unchanged.
- other finding, major, not in findings.json: Graded cells go beyond what the instruction asks for: Valuation upside and variance cells are required but never requested
  - Change: Same prompt sentence change as another finding (not listed).
