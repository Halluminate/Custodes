# Changes: SpreadsheetBench 2 template-07_03

Fix summary (from the fix record):

The instruction said operating results 'first appear in Q2', while the answer key computes Q1 2016 results and rolls them into the Q2 Start balance sheet. One prompt sentence now states that convention. The GT itself already scores 1.0 locally.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: Verifier fails all three units (score 0.0) because the ground truth contradicts the prompt's instruction on when operating results appear
  - Change: prompt.md: changed the sentence 'The Q1 End balance sheet reflects post-acquisition position only; operating results first appear in Q2.' to 'The Q1 End balance sheet reflects post-acquisition position only; Q1 2016 operating results are first reflected in the Q2 Start balance sheet.' This matches the answer key (Q1 2016 income statement C43:C55 populated, rolled into F22:F31) and removes the reading that Q1 results are zero or that Q2 Start equals Q1 End.
- [F3](../findings.json) (Task Spec): Task instruction ('operating results first appear in Q2') contradicts Ground Truth ('gt_07_03_golden.xlsx') Q1 income statement and Q2 Start balance sheet
  - Change: Same prompt sentence change as verifier-correctness-0.
- [F1](../findings.json) (Task Spec): The instruction contradicts itself on when operating results start, and the all-or-nothing verifier rejects the other reading
  - Change: Same prompt sentence change as verifier-correctness-0.
- [F2](../findings.json) (Verification): Answer key changes balances between the same quarter-end and next-quarter opening
  - Change: Same prompt sentence change as verifier-correctness-0.
- other finding, major, not in findings.json: Undisclosed balance sheet convention for intangible asset amortization between Row 23 (Investment in affiliate) and Row 24 (Intangible assets)
  - Change: verifications[0].parameters.answer_position: 'EquityMethod'!B2:G55 -> 'EquityMethod'!B2:G22,'EquityMethod'!B23:E23,'EquityMethod'!B24:E24,'EquityMethod'!B25:G55 (skips F23, G23, F24, G24). Totals F27/G27 and everything else stay graded. graderGuidance range note updated. Local SB2 scorer with recalc: golden PASS, input + key changes PASS, the same with amortization taken off Intangible assets (F23 = D23+C50, F24 = D24-C51) PASS, untouched input FAIL (mod 0.0).
