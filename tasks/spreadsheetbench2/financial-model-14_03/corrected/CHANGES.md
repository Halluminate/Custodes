# Changes: SpreadsheetBench 2 financial-model-14_03

Fix summary (from the fix record):

The golden failed its own check on 97 near-zero residue cells in NCD (1e-13 noise classed as modifications) and agents also failed on the data-table cells LibreOffice cannot recalculate. I removed the NCD/TL near-zero residue cells and 'DCF_Income Approach'!K27:O31 from answer_position; the golden and a simulated correct solution now score 1.0. Full pass: prompt now states the FY26–FY27 maintenance-capex convention (FY22–FY25 average); C35/H35:J35 growth cells, DCF D42 and Cash Flow D48 left out of answer_position.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F5](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: verifications[0].parameters.answer_position: removed 6,290 near-zero floating-point residue cells (|value| < 1e-6) on the untouched NCD and TL sheets and the 25 data-table cells 'DCF_Income Approach'!K27:O31 (TABLE() results LibreOffice cannot recompute). Locally the golden, an openpyxl-saved golden, and the input with the golden's 219 changed cells copied in all score regression 1.0, modification 1.0; the untouched input scores modification 0.
- [F6](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells is a trivial fail due to unrounded near-zero float comparisons in NCD/TL and frozen data-table formulas
  - Change: verifications[0].parameters.answer_position: removed 6,290 near-zero floating-point residue cells (|value| < 1e-6) on the untouched NCD and TL sheets and the 25 data-table cells 'DCF_Income Approach'!K27:O31 (TABLE() results LibreOffice cannot recompute). Locally the golden, an openpyxl-saved golden, and the input with the golden's 219 changed cells copied in all score regression 1.0, modification 1.0; the untouched input scores modification 0.
- [F2](../findings.json) (Reward): Verifier comparison logic misses round-before-compare, causing 1,664 near-zero floating-point noise cells in NCD and TL to be graded as modification errors
  - Change: answer_position no longer includes the 6,290 NCD/TL cells whose input or golden value is a nonzero residue below 1e-6 (covers all 776 NCD and 888 TL noise 'modification' cells).
- [F1](../findings.json) (Reward): Recalculation step freezes data-table (`TABLE(...)`) formulas to stale input values before LibreOffice recalculates
  - Change: answer_position no longer includes the TABLE() sensitivity block 'DCF_Income Approach'!K27:O31, which the grader freezes before recalculation.
- [F4](../findings.json) (Reward): Ground truth fails its own verifier, so no agent can pass
  - Change: verifications[0].parameters.answer_position: removed 6,290 near-zero floating-point residue cells (|value| < 1e-6) on the untouched NCD and TL sheets and the 25 data-table cells 'DCF_Income Approach'!K27:O31 (TABLE() results LibreOffice cannot recompute). Locally the golden, an openpyxl-saved golden, and the input with the golden's 219 changed cells copied in all score regression 1.0, modification 1.0; the untouched input scores modification 0.
- [F3](../findings.json) (Reward): The golden workbook fails its own verifier after required recalculation
  - Change: verifications[0].parameters.answer_position: removed 6,290 near-zero floating-point residue cells (|value| < 1e-6) on the untouched NCD and TL sheets and the 25 data-table cells 'DCF_Income Approach'!K27:O31 (TABLE() results LibreOffice cannot recompute). Locally the golden, an openpyxl-saved golden, and the input with the golden's 219 changed cells copied in all score regression 1.0, modification 1.0; the untouched input scores modification 0.
- other finding, major, not in findings.json: Undisclosed forecast assumptions and formula conventions in Fixed Asset & Depreciation, Profit & Loss, and Cash Flow
  - Change: Prompt: added one sentence after the Fixed Asset instruction: 'For FY26–FY27, hold Maintenance Capex as % of Revenue at the FY22–FY25 average.' (the GT's L27 =AVERAGE(H27:K27), M27 =L27; no other choice is derivable and every alternative misses the 1% tolerance across hundreds of downstream cells). verifications[0].parameters.answer_position: left out 'Profit & Loss'!C35 (2014-15 growth, GT literal 'NA', no prior year), 'Profit & Loss'!H35:J35 (YTD/Q4 columns, GT blank), 'DCF_Income Approach'!D42 (links J35) and 'Cash Flow'!D48 (2016-17 difference, GT blank though the check row starts there). Grader guidance notes the exclusion. SB2 scorer: golden 1.0, golden with C35 blank / J35 filled / D48 filled 1.0, input plus the golden's 219 changes 1.0, untouched input fails (mod 0).
- other finding, major, not in findings.json: Forecast Maintenance Capex % uses a 4-year average (FY22–FY25) that cannot be derived from the task
  - Change: Prompt: added one sentence after the Fixed Asset instruction: 'For FY26–FY27, hold Maintenance Capex as % of Revenue at the FY22–FY25 average.' (the GT's L27 =AVERAGE(H27:K27), M27 =L27; no other choice is derivable and every alternative misses the 1% tolerance across hundreds of downstream cells).
- other finding, major, not in findings.json: The required FY26–FY27 maintenance-capex forecast assumption is unspecified
  - Change: Prompt: added one sentence after the Fixed Asset instruction: 'For FY26–FY27, hold Maintenance Capex as % of Revenue at the FY22–FY25 average.' (the GT's L27 =AVERAGE(H27:K27), M27 =L27; no other choice is derivable and every alternative misses the 1% tolerance across hundreds of downstream cells).
- other finding, major, not in findings.json: Revenue-growth range starts at 2014-15, which has no prior year, and the GT requires the literal text 'NA'
  - Change: verifications[0].parameters.answer_position: left out 'Profit & Loss'!C35 (2014-15 growth, GT literal 'NA', no prior year), 'Profit & Loss'!H35:J35 (YTD/Q4 columns, GT blank), 'DCF_Income Approach'!D42 (links J35) and 'Cash Flow'!D48 (2016-17 difference, GT blank though the check row starts there). Grader guidance notes the exclusion. SB2 scorer: golden 1.0, golden with C35 blank / J35 filled / D48 filled 1.0, input plus the golden's 219 changes 1.0, untouched input fails (mod 0).
