# Changes: SpreadsheetBench 2 debugging-06_07

Fix summary (from the fix record):

The answer key stored #NAME? for the RRI fix in Revenue Build AC41/AC43, forcing an exact formula-text match. Gave those cells a proper RRI formula and computed values, so any correct CAGR formula passes. Full pass: the stale hardcoded DCF sensitivity grids (and summaries on them) are no longer graded.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_06_golden.xlsx

## Fixed

- [F2](../findings.json) (Verification): Answer key stores #NAME? for the RRI fix, so correct fixes that actually calculate are rejected
  - Change: files/gt/gt_06_golden.xlsx 'Revenue Build'!AC41/AC43: formula '=rri(5,W41,AA41)' with cached #NAME? replaced by '=_xlfn.RRI(5,W41,AA41)' / '=_xlfn.RRI(5,W43,AA43)' with real cached values 0.3797297 / 0.7187719. With no error value in the GT the verifier compares values, so any working CAGR fix passes. Local check: patched GT, input+GT formulas, and input with '=(AA41/W41)^(1/5)-1' all PASS
- [F1](../findings.json) (Verification): Correct alternative CAGR formulas are rejected because golden caches contain errors
  - Change: files/gt/gt_06_golden.xlsx 'Revenue Build'!AC41/AC43: formula '=rri(5,W41,AA41)' with cached #NAME? replaced by '=_xlfn.RRI(5,W41,AA41)' / '=_xlfn.RRI(5,W43,AA43)' with real cached values 0.3797297 / 0.7187719. With no error value in the GT the verifier compares values, so any working CAGR fix passes. Local check: patched GT, input+GT formulas, and input with '=(AA41/W41)^(1/5)-1' all PASS
- other finding, major, not in findings.json: Answer key keeps a stale, hardcoded DCF sensitivity table and penalizes rebuilding it, which the instruction asks for
  - Change: verifications[0].parameters.answer_position: 'DCF'!B2:AA50 split to skip the hardcoded sensitivity grids with their WACC axes (M13:Z25, M31:Z43) and the min/mean/max summaries built on them (V5:V7, AA5:AA7). The grids are stale and use a constant PV of UFCF, and there is no single correct rebuild (data table, formula grid or relinked axis), so they are left out rather than added to the key. Grader guidance updated. SB2 scorer with the patched GT: golden 1.0; golden with M19/M37 =WACC!C25 and both grids changed 1.0 (0.973 regression FAIL before); untouched input fails (mod 0).
- other finding, major, not in findings.json: Golden sensitivity tables preserve materially incorrect valuation results
  - Change: Same answer_position change: the miscomputed sensitivity grids are no longer graded, so a corrected rebuild passes.
- other finding, major, not in findings.json: The audit instruction is open-ended, but grading is all-or-nothing against one exact list of fixes
  - Change: Same answer_position change for the sensitivity grids; the other named items are not errors and need no change; the ungraded CHOOSE fixes are covered under another finding (not listed).
