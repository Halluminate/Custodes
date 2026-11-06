# Changes: SpreadsheetBench 2 template-13_03

Fix summary (from the fix record):

The answer key added the Q2 restructuring tax shield with the wrong sign. D32 now adds 21% of the $25 charge like the Q3 row does, and the 11 cells that depend on it were recomputed. Checked locally: the patched key scores 1.0 against itself and a simulated correct answer scores 1.0.

Changed files (in this folder):

- prompt.md
- reference/gt_13_03_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: False negative on unit 1 due to buggy golden workbook formula in FinancialNormalization!D32
  - Change: files/gt/gt_13_03_golden.xlsx: FinancialNormalization!D32 changed from =D12-0.21*25 to =D12+0.21*25 (removing the $25 Q2 COGS charge raises EBT, so tax goes up, as E32 does for Q3). Cached values recomputed in LibreOffice for D32 (28.25), D33, D41, D42, G32, G33, G41, G42, H32, H33, H41, H42. No other cell changed.
- [F2](../findings.json) (Verification): Golden solution has inverted tax adjustment sign for Q2 2024 in cell D32
  - Change: Same GT change as verifier-correctness-0 (D32 sign and dependents).
- [F3](../findings.json) (Verification): Ground truth gets the sign of the Q2 restructuring tax shield wrong, so a correct answer fails the all-or-nothing check
  - Change: Same GT change as verifier-correctness-0 (D32 sign and dependents).
- [F1](../findings.json) (Verification): Ground truth reverses the Q2 restructuring tax-shield adjustment
  - Change: Same GT change as verifier-correctness-0 (D32 sign and dependents).
- other finding, major, not in findings.json: Ambiguity in whether Q2 2025 forecast averages use rolling prior three quarters (E:G) or fixed historical quarters (D:F)
  - Change: Prompt: added one sentence after the forecast instruction: "For Q2 2025, the prior three quarters include the Q1 2025 forecast." Matches the key; no grading change.
- other finding, major, not in findings.json: Forecast method is under-specified, but the binary grader accepts only one exact construction
  - Change: Same prompt sentence clarifying the Q2 2025 window.
