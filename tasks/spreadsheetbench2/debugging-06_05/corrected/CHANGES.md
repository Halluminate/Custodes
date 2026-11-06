# Changes: SpreadsheetBench 2 debugging-06_05

Fix summary (from the fix record):

The answer key kept two broken RRI formulas cached as #NAME?, so the grader fell back to formula text and rejected both untouched and correctly repaired CAGR cells. The answer key now holds a working RRI with its numeric value, so any correct CAGR repair passes. The missing openpyxl is a sandbox issue.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_06_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check fails both untouched and properly fixed Revenue Build!AC41 and AC43 cells due to #NAME? formula prefix mismatch in ground truth
  - Change: ground_truth/gt_06_golden.xlsx: 'Revenue Build'!AC41 and AC43 changed from =rri(5,W41,AA41) / =rri(5,W43,AA43) cached #NAME? to =_xlfn.RRI(5,W41,AA41) / =_xlfn.RRI(5,W43,AA43) with cached values 0.37973 and 0.71877 (the 5-year CAGRs of 10->50 and 40->600); only those two cells' XML changed. A repaired CAGR (RRI or (AA/W)^(1/5)-1) now matches by value; leaving the #NAME? cell still fails. Local replay: golden PASS, openpyxl fix with RRI PASS, fix with explicit CAGR formula PASS.
- [F3](../findings.json) (Verification): Invalid ground-truth formulas in Revenue Build!AC41 and AC43 (#NAME? with =rri vs =_xludf.rri in input) make the task impossible to pass
  - Change: Same GT edit as verifier-correctness-0.
- [F1](../findings.json) (Verification): Hidden extra modification cells: the grader requires the literal RRI formula text in Revenue Build!AC41/AC43, and the ground-truth cached value there is #NAME?
  - Change: Same GT edit as verifier-correctness-0.
- [F2](../findings.json) (Verification): Answer key requires two CAGR formulas to remain broken
  - Change: Same GT edit as verifier-correctness-0.
- other finding, major, not in findings.json: Golden DCF sensitivity tables preserve inconsistent valuations
  - Change: verifications[0].parameters.answer_position: 'DCF'!B2:AA50 -> 'DCF'!B2:AA4,'DCF'!B5:U7,'DCF'!W5:Z7,'DCF'!B8:AA12,'DCF'!B13:M25,'DCF'!AA13:AA25,'DCF'!B26:AA30,'DCF'!B31:M43,'DCF'!AA31:AA43,'DCF'!B44:AA50 (skips the two pasted sensitivity grids N13:Z25, N31:Z43 and their MIN/AVERAGE/MAX cells V5:V7, AA5:AA7), so leaving or rebuilding the grids both pass. Other sheets unchanged. graderGuidance range note updated. Local SB2 scorer with recalc on the critical-pass golden: golden PASS, input + key changes PASS, untouched input FAIL (mod 0.0).
