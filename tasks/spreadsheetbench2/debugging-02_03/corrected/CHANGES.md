# Changes: SpreadsheetBench 2 debugging-02_03

Fix summary (from the fix record):

The key hardcoded new values in the Berk-Hath preferred-stock sensitivity table (G10:K14). Those values are wrong as finance, the task never mentions the table, and the verifier's LibreOffice recalculation cannot reproduce them. Restored the table to its input state, so it is graded as unchanged. Full pass: the key now also deducts the cash consideration from NewCo equity in both OXY merger bridges and fixes the Synergies CVX column (Q11 price link, Q17 cash value, Q24 premium), and the #REF! cells Exhibit 9!N23:P23 are left out of grading.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_02_golden.xlsx

## Fixed

- [F3](../findings.json) (Verification): GT Berk-Hath preferred-stock sensitivity table is wrong and cannot be reproduced, so no correct fix can pass the all-or-nothing check
  - Change: gt_02_golden.xlsx: 'Berk-Hath Investment Package'!G10:K14 restored to the input's TABLE($F$9,$C$12,$Fn,$C$15,x$9) formulas with the input's cached value 11432.1670414077, keeping the golden's cell styles. They are now regression cells. No other cell changed. Golden scores 1.0, the unedited input still scores 0 (modification 0.0).
- [F1](../findings.json) (Verification): The answer key requires a data-table refresh that is outside the stated debugging scope
  - Change: Same GT edit: the data table is no longer a required modification.
- [F2](../findings.json) (Verification): Incorrect answer key for preferred-stock sensitivity analysis
  - Change: Same GT edit: the incorrect hardcoded sensitivity values are removed from the key.
- other finding, minor, not in findings.json: GT leaves #REF! errors in Exhibit 9 even though the task asks for a thorough #REF! fix
  - Change: verifications[0].parameters.answer_position (and the same range list in graderGuidance): 'Exhibit 9'!A1:P30 split into A1:P22, A23:M23, A24:P30, leaving out N23:P23 (=(N20-N18)/(#REF!+N20-N18) in input and key), whose lost reference has no single defensible replacement, so a repair is no longer a regression error. Checked with the real SB2 scorer (verifier's forced LibreOffice recalc, new answer_position): new key 1.0; untouched input plus every key change (XML-level) 1.0; untouched input FAIL (mod 0.0); the previous key now fails only on these corrected cells.
- other finding, major, not in findings.json: Golden merger model double-counts cash consideration
  - Change: files/gt/gt_02_golden.xlsx (built on the critical-pass key, XML-level formula edits): 'Merger Model'!E29 =+E18+E23-E25-E26 -> =+E18+E23-E25-E26-C10*C11 and E57 =E46+E51-E53-E54 -> =E46+E51-E53-E54-C38*C39, so NewCo equity is reduced by the cash paid that D31/D59 already credit to APC holders. Caches recomputed with the verifier's LibreOffice recalc for E29, E30, C29, D29, C31:E31, C32, D32 (E31 55121.65 -> 25367.95 = synergies less break-up fee and costs) and E57, E58, C57, D57, C59:E59, C60, D60 (E59 44531.35 -> 25367.95). No other cell changed. Checked with the real SB2 scorer (verifier's forced LibreOffice recalc, new answer_position): new key 1.0; untouched input plus every key change (XML-level) 1.0; untouched input FAIL (mod 0.0); the previous key now fails only on these corrected cells.
- other finding, major, not in findings.json: Expected Chevron synergy analysis retains contradictory deal arithmetic
  - Change: files/gt/gt_02_golden.xlsx Synergies CVX column, XML-level: Q11 ='Exhibit 3'!$D$14 -> =+'Exhibit 8b'!$D$7 (65 -> 125.99, the CVX price Merger Model!H14 uses), Q17 =Q11*Q15 -> =+Q15*Q16 (32779.5 -> 8194.875, mirrors D17), Q24 =Q17-Q22 -> =+Q19-Q22 (9178.26 -> 9176.01, mirrors D24); dependent caches Q12 12682.39 -> 24582.37 and Q19 45461.89 -> 32777.25 (= Merger Model!I20). Checked with the real SB2 scorer (verifier's forced LibreOffice recalc, new answer_position): new key 1.0; untouched input plus every key change (XML-level) 1.0; untouched input FAIL (mod 0.0); the previous key now fails only on these corrected cells.
