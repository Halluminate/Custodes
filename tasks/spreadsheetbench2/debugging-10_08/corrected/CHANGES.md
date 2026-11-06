# Changes: SpreadsheetBench 2 debugging-10_08

Fix summary (from the fix record):

Fixed the golden's leftover sign bug at Model!D169, recalculated the golden with the grader's LibreOffice pipeline, and removed the cells that depend on the circular cash/debt loop from answer_position. LibreOffice cannot converge those cells to one stable value.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_10_golden.xlsx

## Fixed

- [F4](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells fails even on the golden workbook due to single-pass LibreOffice iterative recalculation divergence and penalizes valid bug fixes
  - Change: gt_10_golden.xlsx: Model!D169 changed from ='FY2024A (CF)'!O37/Mil to =-'FY2024A (CF)'!O37/Mil (C169, E169 and F169 already negate), then the whole file was recalculated with the verifier's own LibreOffice pipeline so its cached values match what the grader produces. verifications[0].parameters.answer_position: the 'Model' and 'P&L Summary' ranges are split to skip the 237 cells that sit in or downstream of the iterative circular block (Model I:M rows 121-207, AV:AX rows 20-43 and their links, P&L Summary R7:T8 and G40:K41). Found by formula dependency analysis. These cells converge to different values depending on the cached starting state, so no output can match them reliably. Checked locally: the input with the 23 golden sign edits plus D169 applied with openpyxl (no cached values) scores 1.0, the corrected golden scores 1.0, and the untouched input scores 0.
- [F3](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: The golden now scores 1.0 on the cell check (same GT recalculation and answer_position change).
- [F2](../findings.json) (Reward): The ground-truth workbook fails its own verifier: 167 modification cells don't survive LibreOffice recalculation because the circular debt and cash model never converged
  - Change: Golden recalculated in LibreOffice and the unconverged circular cells removed from answer_position.
- [F1](../findings.json) (Reward): The golden workbook fails its own full-weight verifier after recalculation
  - Change: Same: the golden caches are now a LibreOffice-recalculated state, and the circular-dependent cells (e.g. J196) are no longer compared.
- other finding, major, not in findings.json: The broken Quick Lookup fix only passes if the agent rewrites the display labels too; other valid fixes are rejected
  - Change: verifications[0].parameters.answer_position: 'P&L Summary'!B46:E51 split into B46:E47, C48:D50, B51:E51, leaving out the label/key cells B48:B50 and E48:E50, and the lookup results F48:F50 added back (stable, not in the circular block). Any lookup repair that returns the right values now passes. Local scorer: input + the key's sign fixes with only E48:E50 changed (B48:B50 left as input) PASS under the new answer_position, FAIL (B48:B50) under the old.
- other finding, major, not in findings.json: The verifier omits a worksheet containing material expected corrections
  - Change: verifications[0].parameters.answer_position: added 'BBC -- Backcountry + SAIL'!B2:M14 (inputs from Model!E20:E28, outside the circular block). Local scorer: patched golden PASS; input + all key fixes PASS; same without the BBC E12 sign fix FAIL (mod 0.9907: E12, G12, G13, E14, G14).
- other finding, major, not in findings.json: The vague 'audit and fix this file thoroughly' prompt is graded all-or-nothing against one hidden set of 23 edits
  - Change: Same answer_position addition as another finding (not listed): the key's BBC E12 sign fix is now graded.
