# Changes: SpreadsheetBench 2 debugging-08_09

Fix summary (from the fix record):

The prompt asks for a thorough audit, but the key fixed only the 27 planted relative/absolute cells. The key now also fixes the errors QA named: R84, C90, M27/R27, I62:L62 Capex, R72 and 'Revenue Build'!J8. C36:H36 leaves answer_position because no single D&A source is defensible.

Changed files (in this folder):

- grading.json (verifier parameters)
- reference/gt_08_golden.xlsx

## Fixed

- [F3](../findings.json) (Verification): Prompt instructs agent to fix all formula, reference, and calculation errors, but ground truth only fixes 27 relative/absolute reference cells and penalizes fixing other broken formulas and typos
  - Change: gt_08_golden.xlsx now also fixes the errors QA named ('Operating Model + DCF' unless noted; 78 dependent cached values rewritten from the verifier's LibreOffice recalc): R84 =R83-M83 (was =R847-M83); C90 tax rate 0.3 (was -0.3); M27 =M26/M4 and R27 =R26/R4 (were dividing by COGS row 7); I62:L62 Capex =-'Key Stats'!G21..J21 (were 'IS Quarters'!E69:H69 depreciation; G:J are the same quarters as I:L, so M62 = 44.85 matches the FY2025 capex in 'Key Stats'!I46, while the finding's E21:H21 would be two quarters early); R72 DSO =AVERAGE(M72,H72,C72:G72) like R75/R78 (was E72:G72); 'Revenue Build'!J8 274.758 (was 264.758, so J17 = 1060.11 matches 'IS Quarters'!D3 and I8:L8 sum to the FY2024 total in M8). Left out of answer_position: 'Operating Model + DCF'!C36:H36 (D&A points at the empty 'IS Annual' row 75 and that sheet has no D&A line, so the CFS D&A row and the IS Quarters depreciation row are both plausible sources; nothing depends on these cells). Checked with the real SB2 scorer: new key vs itself 1.0, input plus all key fixes 1.0, untouched input 0.0, planted-only fixes (original key) 0.0 (expected).
- [F2](../findings.json) (Verification): Answer key keeps a broken cell reference (R847) that the instruction explicitly asks the agent to fix
  - Change: 'Operating Model + DCF'!R84 =R83-M83 in the key (was =R847-M83); dependents recalculated. Checked with the real SB2 scorer: new key vs itself 1.0, input plus all key fixes 1.0, untouched input 0.0, planted-only fixes (original key) 0.0 (expected).
- [F1](../findings.json) (Verification): Answer key only fixes the planted reference errors and keeps other obvious errors (e.g., negative 2025 tax rate in C90), so correct fixes are rejected
  - Change: In the key: 'Operating Model + DCF'!C90 0.3 (was -0.3), M27 =M26/M4 and R27 =R26/R4, R72 =AVERAGE(M72,H72,C72:G72) like R75; dependents recalculated. Checked with the real SB2 scorer: new key vs itself 1.0, input plus all key fixes 1.0, untouched input 0.0, planted-only fixes (original key) 0.0 (expected).
- [F4](../findings.json) (Verification): The answer key penalizes correcting an obvious broken working-capital reference
  - Change: 'Operating Model + DCF'!R84 =R83-M83 in the key; dependents recalculated. Checked with the real SB2 scorer: new key vs itself 1.0, input plus all key fixes 1.0, untouched input 0.0, planted-only fixes (original key) 0.0 (expected).
