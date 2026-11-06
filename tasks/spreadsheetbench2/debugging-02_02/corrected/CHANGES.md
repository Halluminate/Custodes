# Changes: SpreadsheetBench 2 debugging-02_02

Fix summary (from the fix record):

Three unchanged INDEX/MATCH formulas were stored as single-cell array formulas in the golden, so identical formulas failed the formula-mode check; they are now plain formulas in the GT. The Berk-Hath dividend-rate sensitivity grid (G10:K14) holds self-inconsistent Excel data-table values that no output can reproduce, so that block is removed from answer_position. The key now also fixes Synergies!Q17 (cash value uses the $16.25 cash offer), and the #REF! cells Exhibit 9!N23:P23 and the DCF!E32 net-debt label are no longer compared.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_02_golden.xlsx

## Fixed

- [F1](../findings.json) (Reward): Three unchanged INDEX/MATCH formulas are stored as array formulas in the answer key, so the agent must convert them to CSE array formulas to pass
  - Change: gt_02_golden.xlsx: DCF!G9, WACC!C7, WACC!C19 changed from <f t="array" ref=...> to plain <f> with identical text and cached value (XML edit, nothing else touched; WACC!D14, an array formula in both input and GT, left as is). These cells are now regression cells that match the input formulas.
- [F2](../findings.json) (Reward): Correct unchanged formulas fail grading solely because of array-formula serialization
  - Change: Same GT edit (array-formula wrapper removed from DCF!G9, WACC!C7, WACC!C19).
- [F3](../findings.json) (Verification): Golden Berkshire dividend-sensitivity matrix contains 20 incorrect graded values
  - Change: Verifier parameter answer_position: "'Berk-Hath Investment Package'!B2:K44" split into B2:F44, G2:K9 and G15:K44, dropping only the dividend-rate data-table grid G10:K14 whose golden values contradict the sheet's own model (rows 10/13 and 11/12 identical, I12 10429.31 vs base case 11468.40) and cannot be produced because the grader freezes data-table caches. Same range change applied to the range list in grader_guidance.md.
- [F4](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells trivially fails (scores 0.0 on all units and even on a perfect fix of the input workbook) due to ArrayFormula comparison bug and frozen data-table mismatch
  - Change: Both edits above together (array-formula GT fix + G10:K14 excluded). Local grade with the real verifier: input plus the 11 intended hardcode fixes (DCF!J15:R15, Synergies!D11, Merger Model!C42) scores reg 1.0 / mod 1.0 (was mod 0.7807, 25 errors); golden scores 1.0/1.0.
- other finding, major, not in findings.json: Full-audit grading accepts unresolved reference errors and unreconciled cash consideration
  - Change: files/gt/gt_02_golden.xlsx (built on the critical-pass key; XML edit of one formula): Synergies!Q17 'Cash Purchase Value' =Q11*Q15 -> =Q16*Q15 (the $16.25 cash offer price, not the CVX share price); caches of Q17, Q19, Q24 set to the recalculated 8194.875, 20877.26, -15406.36, nothing else changed. verifications[0].parameters.answer_position (and the same range list in graderGuidance): 'Exhibit 9'!A1:P30 split into A1:P22, A23:M23, A24:P30, leaving out N23:P23, whose #REF! has no single defensible replacement. Checked with the real SB2 scorer (formula mode, new answer_position): new key 1.0; untouched input plus all key changes 1.0; untouched input 0.0 (mod 0.8621); the previous key now fails only on Synergies!Q17.
- other finding, major, not in findings.json: The task asks for a thorough open-ended audit, but the grader checks only 11 specific edits and fails a run that changes more than about 0.2% of the other cells
  - Change: answer_position (and guidance range list): 'DCF'!B1:Z35 split into B1:Z31, B32:D32, F32:Z32, B33:Z35, leaving out only the label DCF!E32 '(+) Net Debt' (the model subtracts it in R33), since a relabel has no single text that formula mode could match. Checked with the real SB2 scorer (formula mode, new answer_position): new key 1.0; untouched input plus all key changes 1.0; untouched input 0.0 (mod 0.8621); the previous key now fails only on Synergies!Q17.
