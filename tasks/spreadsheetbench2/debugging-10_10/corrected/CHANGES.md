# Changes: SpreadsheetBench 2 debugging-10_10

Fix summary (from the fix record):

The golden failed its own cell check because the workbook's circular debt/cash-sweep loop recalculates to different values in LibreOffice each time. I removed those unstable blocks from the graded ranges; the real edits are still graded and the golden now passes. Full pass: the P&L Summary lookup labels B48:B50/E48:E50, the 33 unrecoverable #REF! cells and FY2026B (IS)!C33 are no longer compared, so other valid repairs are not failed.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F5](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells is a trivial fail (cannot pass even on the ground-truth golden workbook)
  - Change: verifications[0].parameters.answer_position: carved out of the graded ranges the blocks driven by the workbook's iterative (circular) debt/cash-sweep loop, whose values LibreOffice's forced recalc does not converge to the same point twice: Model!I121:M199, R20:T41, X20:X41, AL20:AN41, AW20:AW41; 'P&L Summary'!R7:T8, G40:K41; '4-Wall Analysis'!BS5:DD17 (1,081 of 294,669 cells; all 266 cells that differed across repeated recalcs are inside). The 9 real edits (Model D16, F218, P&L Summary B48:B50/E48:E50, FY24SAIL15 R10) and their dependents are still graded. Local checks with the verifier's score_workbooks: golden PASS (was 0.0, mod 0.4339); input + the 9 golden edits PASS; untouched input still FAILS (mod 0.035). graderGuidance range list updated to match.
- [F4](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: verifications[0].parameters.answer_position: carved out of the graded ranges the blocks driven by the workbook's iterative (circular) debt/cash-sweep loop, whose values LibreOffice's forced recalc does not converge to the same point twice: Model!I121:M199, R20:T41, X20:X41, AL20:AN41, AW20:AW41; 'P&L Summary'!R7:T8, G40:K41; '4-Wall Analysis'!BS5:DD17 (1,081 of 294,669 cells; all 266 cells that differed across repeated recalcs are inside). The 9 real edits (Model D16, F218, P&L Summary B48:B50/E48:E50, FY24SAIL15 R10) and their dependents are still graded. Local checks with the verifier's score_workbooks: golden PASS (was 0.0, mod 0.4339); input + the 9 golden edits PASS; untouched input still FAILS (mod 0.035). graderGuidance range list updated to match.
- [F2](../findings.json) (Reward): Golden solution fails its own verifier (score 0.0, 167 cell errors) due to un-recalculated Excel iterative cache vs. LibreOffice recalculation of output
  - Change: verifications[0].parameters.answer_position: carved out of the graded ranges the blocks driven by the workbook's iterative (circular) debt/cash-sweep loop, whose values LibreOffice's forced recalc does not converge to the same point twice: Model!I121:M199, R20:T41, X20:X41, AL20:AN41, AW20:AW41; 'P&L Summary'!R7:T8, G40:K41; '4-Wall Analysis'!BS5:DD17 (1,081 of 294,669 cells; all 266 cells that differed across repeated recalcs are inside). The 9 real edits (Model D16, F218, P&L Summary B48:B50/E48:E50, FY24SAIL15 R10) and their dependents are still graded. Local checks with the verifier's score_workbooks: golden PASS (was 0.0, mod 0.4339); input + the 9 golden edits PASS; untouched input still FAILS (mod 0.035). graderGuidance range list updated to match.
- [F3](../findings.json) (Reward): Golden workbook fails the verifier's mandatory recalculation
  - Change: verifications[0].parameters.answer_position: carved out of the graded ranges the blocks driven by the workbook's iterative (circular) debt/cash-sweep loop, whose values LibreOffice's forced recalc does not converge to the same point twice: Model!I121:M199, R20:T41, X20:X41, AL20:AN41, AW20:AW41; 'P&L Summary'!R7:T8, G40:K41; '4-Wall Analysis'!BS5:DD17 (1,081 of 294,669 cells; all 266 cells that differed across repeated recalcs are inside). The 9 real edits (Model D16, F218, P&L Summary B48:B50/E48:E50, FY24SAIL15 R10) and their dependents are still graded. Local checks with the verifier's score_workbooks: golden PASS (was 0.0, mod 0.4339); input + the 9 golden edits PASS; untouched input still FAILS (mod 0.035). graderGuidance range list updated to match.
- other finding, major, not in findings.json: The grader accepts only one exact label text for the P&L Summary lookup fix and rejects other valid fixes
  - Change: verifications[0].parameters.answer_position: 'P&L Summary'!B42:T51 split to leave out the label/key cells B48:B50 and E48:E50; the lookup results F48:F50 stay graded. graderGuidance range text updated. Local SB2 grade (new ranges): golden PASS 1.0/1.0; golden with only the E48:E50 keys fixed (B48:B50 left as input) PASS (FAIL on B48:B50 under the old ranges); untouched input FAIL (mod 0.037).
- other finding, major, not in findings.json: Undisclosed target errors and contradictory filename ('Unit Mismatch_input.xlsx') vs. vague generic prompt
  - Change: verifications[0].parameters.answer_position: named errors with no single defensible correction are no longer compared: the 33 '=#REF!' cells ('FY2024A (Earnings)'!C5:N5, 'FY2027P (IS)'!K33:N33, 'FY2027P (Earnings)'!A1, 'FY2028P (IS)'!A3:A4, C9, L9, C33:N33; the lost targets cannot be recovered) and 'FY2026B (IS)'!C33; plus the B48:B50/E48:E50 carve-out of another finding (not listed). Key unchanged. graderGuidance range text updated.

## Confirmed findings not fixed

- [F1](../findings.json): System Python is not executable by the `model` user (`Permission denied` on `/usr/bin/python3.12`), breaking the advertised Python environment
  - Reason: infra
