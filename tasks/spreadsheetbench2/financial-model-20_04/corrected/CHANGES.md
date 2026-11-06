# Changes: SpreadsheetBench 2 financial-model-20_04

Fix summary (from the fix record):

The prompt asks for Return on Total Assets for FY24-FY27 only, but the key also graded 42 monthly cells and their Summary links. Those monthly cells are now outside the compared range, so filling them or not both pass, while the annual cells stay graded.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells fails all three units (score=0) for omitting unrequested monthly Return on Total Assets cells
  - Change: verifications[0].parameters.answer_position: 'Summary'!B2:AW122 split into B2:AW105, B106:G106, B107:AW122 and 'Ratio Analysis'!B2:AW49 into B2:AW17, B18:G18, B19:AW49, so the unrequested monthly Return on Total Assets cells (Ratio Analysis H18:AW18) and their Summary H106:AW106 links are not compared; the requested FY24-FY27 cells C18:F18 (and Summary C106:F106) stay graded. Local replay: golden PASS; golden with H18:AW18 blanked PASS (was mod 0.9714 FAIL); untouched input still FAIL.
- [F2](../findings.json) (Task Spec): Ground truth grades monthly Return on Total Assets (Jul-24 to Dec-27) despite prompt only asking for annual FY24–FY27
  - Change: Same answer_position change as verifier-correctness-0.
- [F1](../findings.json) (Verification): Return on Total Assets: the prompt asks for annual FY24–FY27 only, but the answer key also requires all 42 monthly cells
  - Change: Same answer_position change as verifier-correctness-0.
- [F3](../findings.json) (Task Spec): Grader requires monthly Return on Total Assets that the instructions request only annually
  - Change: Same answer_position change as verifier-correctness-0.
