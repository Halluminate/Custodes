# Changes: FINCH task-088

Fix summary (from the fix record):

The reference workbook's Spending Efficiency and Debt Service Burden columns now follow the formulas stated in the prompt, recomputed from its own RawData sheet. Full pass: the guidance now notes that 'Federal Budget' is undefined (reference = receipts, other standard readings accepted) and that metrics derived from unrounded source data are accepted alongside the reference's rounded-input values.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_88_ref_0.xlsx

## Fixed

- [F3](../findings.json) (Verification): Ground truth reference workbook gt_88_ref_0.xlsx computes Spending Efficiency and Debt Service Burden on Sheet3_Fiscal_Indicators using wrong formulas that contradict problem.py
  - Change: gt_88_ref_0.xlsx Sheet3_Fiscal_Indicators: E2:E11 recomputed as Budget/Spending x 100 (2 dp) and F2:F11 as Interest/Debt x 100 (4 dp) from the GT's own RawData, e.g. FY2015 E2 100 -> 88.08, F2 6.7692 -> 1.2121; FY2024 E11 100 -> 72.89, F11 17.8862 -> 2.481. No other cell changed.
- [F4](../findings.json) (Verification): Ground truth uses the wrong formula for Spending Efficiency
  - Change: Spending Efficiency part of the same edit: Sheet3_Fiscal_Indicators E2:E11 = Budget/Spending x 100.
- [F1](../findings.json) (Verification): Ground truth Debt Service Burden is Interest/Budget, not the stated Interest/Debt
  - Change: Debt Service Burden part of the same edit: Sheet3_Fiscal_Indicators F2:F11 = Interest/Debt x 100.
- [F2](../findings.json) (Verification): Reference answer contradicts both fiscal-indicator formulas
  - Change: Same edit to Sheet3_Fiscal_Indicators E2:F11.
- other finding, major, not in findings.json: Prompt requests 'the federal Budget (trillion)' in RawData without input files, but ground truth gt_88_ref_0.xlsx actually stores U.S. Federal Revenue/Receipts
  - Change: graderGuidance: added a task note after the opening paragraph saying the instruction does not define 'Federal Budget', the reference uses total federal receipts, and another clearly used standard reading (e.g. total outlays or the enacted budget) is also accepted when the derived sheets follow from its own RawData by the stated formulas. Prompt, reference and verifier unchanged.
- other finding, major, not in findings.json: 'Federal Budget' is undefined; GT silently treats it as federal receipts (revenue)
  - Change: graderGuidance: added a task note after the opening paragraph saying the instruction does not define 'Federal Budget', the reference uses total federal receipts, and another clearly used standard reading (e.g. total outlays or the enacted budget) is also accepted when the derived sheets follow from its own RawData by the stated formulas. Prompt, reference and verifier unchanged.
- other finding, major, not in findings.json: The reference silently interprets 'Federal Budget' as actual federal receipts
  - Change: graderGuidance: added a task note after the opening paragraph saying the instruction does not define 'Federal Budget', the reference uses total federal receipts, and another clearly used standard reading (e.g. total outlays or the enacted budget) is also accepted when the derived sheets follow from its own RawData by the stated formulas. Prompt, reference and verifier unchanged.
- other finding, major, not in findings.json: Reference derived metrics are computed from 2-decimal rounded raw data; precise source data gives values outside tolerance
  - Change: graderGuidance: same task note also says the reference derives Sheets 2-5 from RawData rounded to two decimals and that values derived from unrounded source figures are equally correct, with the FY2018 (23.78 vs 26.92) and FY2021 (1.99 vs 0.00) interest-growth examples (checked against OMB Table 3.2 net interest).
- other finding, major, not in findings.json: Reference growth rates depend on an undisclosed intermediate-rounding convention
  - Change: graderGuidance: same task note also says the reference derives Sheets 2-5 from RawData rounded to two decimals and that values derived from unrounded source figures are equally correct, with the FY2018 (23.78 vs 26.92) and FY2021 (1.99 vs 0.00) interest-growth examples (checked against OMB Table 3.2 net interest).
