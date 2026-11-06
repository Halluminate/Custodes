# Changes: SpreadsheetBench 2 debugging-06_03

Fix summary (from the fix record):

Removed two un-recoverable to-do notes and the free-wording labels of the restored rows from grading, stated in one prompt sentence that deleted rows go back in place, and fixed the golden RRI cells so they hold a value instead of #NAME?. Full pass: the moved to-do notes with typos, the unfinished PTA terminal value and the pasted DCF sensitivity grids are also left out of grading.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_06_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): The grader cannot be passed: the answer key needs free-text notes that appear nowhere in the input
  - Change: answer_position: excluded the two golden to-do notes absent from the input, 'Revenue Build'!W33 and 'Supporting Schedules'!U52 (no formula references them).
- [F2](../findings.json) (Task Spec): The answer key expects three deleted rows rebuilt with exact labels at exact row positions, and the prompt says nothing about deleted rows
  - Change: Prompt: added one sentence after the error list: 'Where a deleted row has left broken references, restore that row at its original position.' answer_position also excludes the restored rows' label/unit cells ('Revenue Build'!B33, 'Operating Model'!B23, 'Supporting Schedules'!B52 and D52) so 'D&A' vs 'Depreciation' wording does not decide the grade.
- [F3](../findings.json) (Verification): The answer key leaves #NAME? cached in the RRI CAGR cells, so only the exact formula text passes
  - Change: gt_06_golden.xlsx 'Revenue Build'!AC41 and AC43: formula 'rri(...)' (unknown function, cached #NAME?) changed to '_xlfn.RRI(5,W41,AA41)' / '_xlfn.RRI(5,W43,AA43)', the stored form of Excel's RRI, and caches recalculated to 0.3797 and 0.7188. With a numeric golden value the verifier compares values, so any correct CAGR formula passes. No other cell changed.
- [F1](../findings.json) (Verification): Answer key penalizes repairing two CAGR formula errors
  - Change: gt_06_golden.xlsx 'Revenue Build'!AC41 and AC43: formula 'rri(...)' (unknown function, cached #NAME?) changed to '_xlfn.RRI(5,W41,AA41)' / '_xlfn.RRI(5,W43,AA43)', the stored form of Excel's RRI, and caches recalculated to 0.3797 and 0.7188. With a numeric golden value the verifier compares values, so any correct CAGR formula passes. No other cell changed.
- other finding, major, not in findings.json: Fixing the typos the prompt asks for in shifted note cells fails the all-or-nothing check
  - Change: verifications[0].parameters.answer_position: the three moved to-do notes with typos, 'Revenue Build'!W36, W46 and 'Operating Model'!M39, are left out (ranges split around them), so cleaning up or keeping the typos both pass. The J25:L25 vs M25:S25 tax sign mix needs no change: J23:L23 EBIT is negative, so both forms give 0 and the values-mode check cannot tell them apart. Locally: golden PASS (reg 1.0, mod 1.0); golden with the typos fixed PASS.
- other finding, major, not in findings.json: The answer key keeps another unfixed error in the PTA terminal value: R26 is 0 and R39 is meaningless
  - Change: verifications[0].parameters.answer_position: 'PTA'!B2:R39 split into B2:R23 and B24:Q39, leaving out R24:R39. R24 (Median EV/EBIT Multiple) is blank in input and key and the precedents table has only one (negative) EV/EBIT figure, so the terminal value has no single defensible repair. R22 (the restored PV of UFCF reference) stays graded. Locally: golden with R24 filled (=MEDIAN(H4:H12)) PASS.
- other finding, major, not in findings.json: Grader protects inconsistent hardcoded DCF sensitivity results
  - Change: verifications[0].parameters.answer_position: 'DCF'!B2:AA50 split to leave out the pasted sensitivity grids N13:Z25 and N31:Z43 and their MIN/AVERAGE/MAX summaries V5:V7 and AA5:AA7 (no other formula reads them). They are values pasted from an Excel data table; a live rebuild (TABLE()) does not recalculate in LibreOffice, so there is no single correction the key can hold. Locally: golden with both grids changed (x1.08, x0.93) PASS under the new answer_position.
