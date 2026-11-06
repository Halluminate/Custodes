# Changes: SpreadsheetBench 2 financial-model-17_01

Fix summary (from the fix record):

The answer key left the requested 2014F-2018F tax provision blank and set EBITDA equal to EBIT. Added the tax formulas, made EBITDA add back D&A, and recalculated the whole workbook. Balance sheet and cash flow checks stay at 0.

Changed files (in this folder):

- reference/gt_17_FMCG_golden.xlsx

## Fixed

- [F6](../findings.json) (Verification): SpreadsheetBench 2 official cell check: Verifier fails all three units (score=0.0) due to defective ground-truth workbook on Tax Provision and EBITDA
  - Change: gt_17_FMCG_golden.xlsx: Financials!K38:O38 = -K35*K39 (K38 = -2123.06), Financials!E17:O17 = E10+E14-E21 (E17 = 6746). Recalculated in LibreOffice, so the downstream Financials, Valuation, Ratio_Analysis and Graphical_representation values follow. No other formulas changed.
- [F5](../findings.json) (Verification): Golden workbook omits required 2014F–2018F Tax Provision (Financials!K38:O38), penalizing agents that follow the prompt instruction
  - Change: gt_17_FMCG_golden.xlsx: Financials!K38:O38 set to =-K35*K39 ... =-O35*O39.
- [F3](../findings.json) (Verification): Golden workbook sets EBITDA equal to EBIT (Financials!E17:O17 = E14+E10), ignoring Depreciation & Amortization in Row 21
  - Change: gt_17_FMCG_golden.xlsx: Financials!E17:O17 set to =E10+E14-E21 ... (EBIT plus D&A).
- [F1](../findings.json) (Verification): The answer key leaves forecast Tax Provision blank, so an agent that does the requested calculation fails the only verifier
  - Change: Same GT edit as F5 (forecast tax provision added).

## Confirmed findings not fixed

- [F2](../findings.json): Ground truth omits the explicitly required forecast tax provisions
  - Reason: duplicate-of:F5
- [F4](../findings.json): The answer key equates EBITDA with EBIT despite nonzero depreciation
  - Reason: duplicate-of:F3
