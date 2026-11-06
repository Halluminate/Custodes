# Changes: SpreadsheetBench 2 template-07_02

Fix summary (from the fix record):

The answer key booked the investment on an unlabeled row and never added equity income to it, leaving the year-end balance sheet 3,900 out; the key now books it on 'Investment in affiliate' and balances.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_07_02_golden.xlsx

## Fixed

- [F5](../findings.json) (Verification): SpreadsheetBench 2 official cell check: Verifier fails valid equity method balance sheet completions (false negative / trivial fail) due to corrupted Row 22/23 in ground truth
  - Change: gt_07_02_golden.xlsx, sheet EquityMethod: cleared the stray unlabeled row 22 (E22 '=D10', F22, H22), completed the 'Investment in affiliate' row 23 with F23 '=SUM(D23:E23)' (6,000), G23 '=D45' (3,900 equity income) so H23 = 9,900; Year-End Total Assets H27 now 235,400 = Total L&E H33. No other cell changed; caches recalculated and the GT scores 1.0 on its own verifier.
- [F4](../findings.json) (Verification): Corrupted ground-truth workbook shifts 'Investment in affiliate' values onto blank Row 22 and omits affiliate equity income from Row 23, resulting in an unbalanced Year-End Balance Sheet
  - Change: gt_07_02_golden.xlsx, sheet EquityMethod: cleared the stray unlabeled row 22 (E22 '=D10', F22, H22), completed the 'Investment in affiliate' row 23 with F23 '=SUM(D23:E23)' (6,000), G23 '=D45' (3,900 equity income) so H23 = 9,900; Year-End Total Assets H27 now 235,400 = Total L&E H33. No other cell changed; caches recalculated and the GT scores 1.0 on its own verifier.
- [F3](../findings.json) (Verification): The ground-truth balance sheet doesn't balance at year end: equity income is never added to the investment
  - Change: gt_07_02_golden.xlsx, sheet EquityMethod: cleared the stray unlabeled row 22 (E22 '=D10', F22, H22), completed the 'Investment in affiliate' row 23 with F23 '=SUM(D23:E23)' (6,000), G23 '=D45' (3,900 equity income) so H23 = 9,900; Year-End Total Assets H27 now 235,400 = Total L&E H33. No other cell changed; caches recalculated and the GT scores 1.0 on its own verifier.
- [F1](../findings.json) (Verification): The ground truth books the 6,000 investment in an unlabeled row 22 instead of the 'Investment in affiliate' row the instructions name
  - Change: gt_07_02_golden.xlsx, sheet EquityMethod: cleared the stray unlabeled row 22 (E22 '=D10', F22, H22), completed the 'Investment in affiliate' row 23 with F23 '=SUM(D23:E23)' (6,000), G23 '=D45' (3,900 equity income) so H23 = 9,900; Year-End Total Assets H27 now 235,400 = Total L&E H33. No other cell changed; caches recalculated and the GT scores 1.0 on its own verifier.
- [F2](../findings.json) (Verification): Answer key misplaces the investment and leaves the year-end balance sheet unbalanced
  - Change: gt_07_02_golden.xlsx, sheet EquityMethod: cleared the stray unlabeled row 22 (E22 '=D10', F22, H22), completed the 'Investment in affiliate' row 23 with F23 '=SUM(D23:E23)' (6,000), G23 '=D45' (3,900 equity income) so H23 = 9,900; Year-End Total Assets H27 now 235,400 = Total L&E H33. No other cell changed; caches recalculated and the GT scores 1.0 on its own verifier.
- other finding, major, not in findings.json: Undisclosed Total Assets / Total L&E column convention for 'Jan Changes' and 'Year Changes' columns (E27, G27, E33, G33)
  - Change: verifications[0].parameters.answer_position: 'EquityMethod'!C2:K60 -> 'EquityMethod'!C2:K26,'EquityMethod'!C27:D27,'EquityMethod'!F27,'EquityMethod'!H27:K27,'EquityMethod'!C28:K32,'EquityMethod'!C33:D33,'EquityMethod'!F33,'EquityMethod'!H33:K33,'EquityMethod'!C34:K60 (skips E27, G27, E33, G33). graderGuidance range note updated. Local SB2 scorer with recalc on the critical-pass golden: golden PASS, input + key changes PASS, the same with SUM totals in E27/G27/E33/G33 PASS, untouched input FAIL (mod 0.0).
