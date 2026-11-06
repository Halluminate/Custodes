# Changes: SpreadsheetBench 2 debugging-08_02

Fix summary (from the fix record):

The prompt asks for a thorough audit, but the key fixed only the planted hardcodes and kept other real errors QA named. The key now also fixes R84, EBT row 28 interest, C36:H36 D&A links, the K/L margin rows and the Revenue Build S9:V9/S15:V15 case links. Named cells whose repair has several equally natural formula texts (self-referencing OFFSET rows, C98:H98, C111/C125/C138) leave answer_position. Exact-text matching of equivalent formulas (INDEX/MATCH vs direct links) is still a verifier-code limitation.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_08_golden.xlsx

## Fixed

- [F6](../findings.json) (Reward): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check falsely fails valid formula fixes across all 3 units due to rigid formula-string matching and unfixed bugs in GT
  - Change: Partial. gt_08_golden.xlsx now also fixes the errors QA named, on top of the 15 planted hardcode fixes (formula mode, so the key's formula text is what is graded; cached values were also refreshed from the verifier's LibreOffice recalc, 113 cells): 'Operating Model + DCF'!R84 =R847-M83 -> =R83-M83; EBT row 28 C28:V28 =X20-X26 -> =X20-X23-X26 (interest subtracted; F28 now equals 'IS Annual'!F24 pretax income); C36:H36 ='IS Annual'!C75:H75 (empty) -> =CFS!E4:J4 (D&A matched by fiscal year); K9:L9, K12:L12, K15:L15 =K41/K47/K53 (empty) -> =K8/K4, =K11/K4, =K14/K4 like I:J; 'Revenue Build'!S9:V9 =S37 (Base row) -> =S35 and S15:V15 =S43 -> =S41 (the Case Selection rows that X:AA and the planted S6 use). Left out of answer_position because the repair has no single defensible formula text: the self-referencing case-selection OFFSET rows ('Operating Model + DCF'!N41:V41, N47:V47, N53:V53; 'Revenue Build'!S29:AA29, S35:AA35, S41:AA41; the finding's 'S37/S43' are the Base rows, the OFFSET formulas sit in rows 35 and 41), the hardcoded WACC C98:H98 (link every cell to 'Comps + WACC'!C38 or chain =C98), and the ^5 terminal-value discounting in C111, C125, C138 (^6, ^H97 or /H99 are equally natural). Checked with the real SB2 scorer: new key vs itself 1.0; untouched input plus all key fixes 1.0; untouched input 0.0; planted-only fixes (the old key) now fail (mod 0.2679), as expected. The rejection of equivalent direct links for C108/C113 is a verifier-code limitation (formula mode compares normalised text only) and is not changed.
- [F2](../findings.json) (Verification): Golden workbook (gt_08_golden.xlsx) leaves numerous genuine formula errors and hardcoded values unfixed, penalizing thorough audits
  - Change: gt_08_golden.xlsx now also fixes the errors QA named, on top of the 15 planted hardcode fixes (formula mode, so the key's formula text is what is graded; cached values were also refreshed from the verifier's LibreOffice recalc, 113 cells): 'Operating Model + DCF'!R84 =R847-M83 -> =R83-M83; EBT row 28 C28:V28 =X20-X26 -> =X20-X23-X26 (interest subtracted; F28 now equals 'IS Annual'!F24 pretax income); C36:H36 ='IS Annual'!C75:H75 (empty) -> =CFS!E4:J4 (D&A matched by fiscal year); K9:L9, K12:L12, K15:L15 =K41/K47/K53 (empty) -> =K8/K4, =K11/K4, =K14/K4 like I:J; 'Revenue Build'!S9:V9 =S37 (Base row) -> =S35 and S15:V15 =S43 -> =S41 (the Case Selection rows that X:AA and the planted S6 use). Left out of answer_position because the repair has no single defensible formula text: the self-referencing case-selection OFFSET rows ('Operating Model + DCF'!N41:V41, N47:V47, N53:V53; 'Revenue Build'!S29:AA29, S35:AA35, S41:AA41; the finding's 'S37/S43' are the Base rows, the OFFSET formulas sit in rows 35 and 41), the hardcoded WACC C98:H98 (link every cell to 'Comps + WACC'!C38 or chain =C98), and the ^5 terminal-value discounting in C111, C125, C138 (^6, ^H97 or /H99 are equally natural). Checked with the real SB2 scorer: new key vs itself 1.0; untouched input plus all key fixes 1.0; untouched input 0.0; planted-only fixes (the old key) now fail (mod 0.2679), as expected.
- [F5](../findings.json) (Verification): Golden workbook preserves errors that the requested thorough audit must fix
  - Change: Same key change: F28:V28 (with C28:E28), C36:H36, K9:L9/K12:L12/K15:L15 and R84 are all fixed in the key.

## Confirmed findings not fixed

- [F4](../findings.json): Verifier uses exact formula-string matching (mode: formula) and all-or-nothing binary grading against unstated formula syntax conventions
  - Reason: cannot-fix-safely: verify_spreadsheetbench2_cells has no formula-equivalence mode; switching the key's INDEX/MATCH (C108, C113) to direct links would only fail agents that use INDEX/MATCH instead.
- [F1](../findings.json): The verifier only accepts the golden file's exact INDEX/MATCH formula text, so correct links to the same cells score 0
  - Reason: duplicate-of:F4
- [F3](../findings.json): Formula grading rejects mathematically equivalent repairs without specifying required syntax
  - Reason: duplicate-of:F4
