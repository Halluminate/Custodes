# Changes: SpreadsheetBench 2 financial-model-07_02

Fix summary (from the fix record):

Recalculated the golden and untouched-reference workbooks in LibreOffice so their cached values no longer carry the old #NAME? XLOOKUP results (the golden now scores 1.0 locally), and named the Inputs rows and sheets behind the area cells in the prompt. The 1,217 cells that hang off the self-referencing Construction Schedule costs and do not settle in one LibreOffice recalculation are left out of answer_position, so an openpyxl-saved output now passes; all requested cells stay graded. The ungraded pre-existing chart stays cannot-fix-safely.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_07_RealEstate_golden.xlsx
- reference/untouched_input_07_02_RealEstate_input.xlsx

## Fixed

- [F8](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells trivially fails all runs (and the golden file itself) due to LibreOffice XLOOKUP recalculation mismatch against stale golden cached values
  - Change: Replaced gt_07_RealEstate_golden.xlsx and untouched_input_07_02_RealEstate_input.xlsx with LibreOffice-recalculated copies (formulas unchanged), so the cached Sales Schedule XLOOKUP chain matches what the verifier's recalculation of a submission produces. Local verify_spreadsheetbench2_cells on the new golden: regression 1.0, modification 1.0.
- [F7](../findings.json) (Verification): Golden gate: the ground-truth deliverable does not score full reward
  - Change: Same golden and reference recalculation; the golden now grades 1.0 locally.
- [F3](../findings.json) (Verification): Golden workbook has stale #NAME? cached values from LibreOffice 7.3 XLOOKUP incompatibility, making the benchmark unpassable under LibreOffice 26.2 recalculation
  - Change: Same golden and reference recalculation, which clears the stale #NAME? caches.
- [F2](../findings.json) (Verification): Ground-truth cached values come from an XLOOKUP that returned #NAME?, so the GT fails its own LibreOffice-recalculated grading and the task cannot be passed
  - Change: Same golden and reference recalculation; Executive Summary!D27 is now keyed at 49.61, the recalculated value.
- [F6](../findings.json) (Verification): Golden workbook fails the problem's own grading procedure
  - Change: Same golden and reference recalculation.
- [F4](../findings.json) (Task Spec): Total and Balance Saleable Area do not exist in Inputs, and the GT maps them to Construction Area and Saleable Area without saying so
  - Change: Prompt: the Sold Area sentence now says to link Total Salable Area to Construction Area and Balance Saleable Area to Saleable Area in Inputs, matching the golden's D8=Inputs!D10 and D10=Inputs!D11.
- [F5](../findings.json) (Task Spec): Misleading terminology in prompt for Saleable Area vs Construction Area and sheet name for Construction Area link
  - Change: Prompt: the area mapping is spelled out as above, and the last sentence now says 'In the Construction Schedule sheet, link Construction Area ...', the sheet whose E5 the golden fills.
- [F1](../findings.json) (Task Spec): Area assumptions and expected answers contradict the task
  - Change: Prompt: the area mapping is spelled out as above, and Amount/sf now divides 'by the sheet's Saleable Area in Sq.ft (E1)', which is the divisor the golden uses (=D9/$E$1).
- other finding, major, not in findings.json: Construction costs depend on circular formulas rather than independent assumptions
  - Change: answer_position (parameters only) and the full grader guidance leave out the 1,217 cells that depend on the self-referencing Construction Schedule D-column costs and do not settle in one LibreOffice recalculation (found by grading the golden re-saved with openpyxl and the input plus key formulas saved with openpyxl; a warm start from the input's caches moves nothing). None of the 19 cells the instruction asks for is dropped. Real SB2 scorer: golden 1.0, golden re-saved with openpyxl 1.0 (was 1,217 errors), input + key formulas saved with openpyxl 1.0, untouched input fails (mod 0.0).
