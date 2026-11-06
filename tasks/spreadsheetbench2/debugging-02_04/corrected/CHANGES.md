# Changes: SpreadsheetBench 2 debugging-02_04

Fix summary (from the fix record):

Removed the 100 what-if data-table grid cells (DCF!V10:Z14 and Berk-Hath Investment Package G10:K14, G18:K22, G26:K30) from the cell check's answer_position. The grader's LibreOffice recalculation cannot reproduce these cells, and the answer key's Berk-Hath values are wrong. The 15 font-colour fixes and everything else are graded as before.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_02_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells consistently scores 0.0 across all runs due to corrupted ground-truth Data Table values in Berk-Hath Investment Package!G10:K14
  - Change: verifications[0].parameters.answer_position: the 'DCF'!B1:Z35 and 'Berk-Hath Investment Package'!B2:K44 ranges are split so they skip the TABLE() grids DCF!V10:Z14, Berk-Hath G10:K14, G18:K22 and G26:K30. Checked locally with the unchanged golden: the input with only the 15 golden font-colour changes (DCF C8:C10, J15:R15, WACC C7, Synergies D36:D37) applied with openpyxl now scores 1.0, the golden scores 1.0 and the untouched input scores 0.
- [F3](../findings.json) (Verification): Corrupted ground-truth sensitivity table values in Berk-Hath Investment Package!G10:K14 and frozen data-table recalculation make 22 of 37 modification cells impossible to pass
  - Change: The 22 corrupted Berk-Hath G10:K14 modification cells are no longer graded, via the same answer_position change.
- [F1](../findings.json) (Reward): Excel data-table (TABLE()) cells cannot be reproduced by the verifier's LibreOffice recalc. GT holds Excel-only values that stay stale, and openpyxl edits wipe them to None, so the task cannot pass.
  - Change: All TABLE() grid cells, which LibreOffice recalculation cannot reproduce, are excluded from answer_position.
- [F2](../findings.json) (Verification): Incorrect sensitivity-table answer key rejects mathematically correct repairs
  - Change: The wrong golden sensitivity values are no longer compared, so a correct table is not penalised.
- other finding, major, not in findings.json: GT applies the Cover-sheet colour legend inconsistently, so a consistent recolour is penalised
  - Change: gt_02_golden.xlsx font colours only (XML: cloned font + xf, no value, formula or other style touched): DCF!R34 ='Exhibit 6'!D33 and Berk-Hath C29 ='Exhibit 5'!B10, C31 ='Exhibit 6'!F32 black -> green 00B050 (Cover: link to a different sheet); Merger Model J23 =I23, J26 =I26 black -> purple 7030A0 and Berk-Hath F12 =C12 blue -> purple (Cover: link in the same sheet). Checked with the real scorer (font_color mode): new golden 1.0; input + all 21 key colour changes 1.0; that plus green on the excluded DCF/WACC cells and a repaired Exhibit 9 row 23 still 1.0; untouched input fails.
- other finding, major, not in findings.json: Undisclosed font-color conventions on cross-sheet expressions and same-sheet links cause regression failures for agents applying the Cover sheet legend
  - Change: gt_02_golden.xlsx font colours only (XML: cloned font + xf, no value, formula or other style touched): DCF!R34 ='Exhibit 6'!D33 and Berk-Hath C29 ='Exhibit 5'!B10, C31 ='Exhibit 6'!F32 black -> green 00B050 (Cover: link to a different sheet); Merger Model J23 =I23, J26 =I26 black -> purple 7030A0 and Berk-Hath F12 =C12 blue -> purple (Cover: link in the same sheet). answer_position: the cells whose correct colour has no single reading are left out: DCF!G13:H14 and H24 (arithmetic on cross-sheet refs; black 'formula' or green 'link' both defensible, the key itself mixes them), WACC!C7's neighbours C14 and D7 (same), and Exhibit 9!N23:P23 (=(N20-N18)/(#REF!+N20-N18): the lost reference has no single defensible replacement). Ranges split: DCF B10:U14 -> B10:U12,B13:F14,I13:U14; DCF B15:Z35 -> B15:Z23,B24:G24,I24:Z24,B25:Z35; WACC B2:M22 -> B2:M6,B7:C7,E7:M7,B8:M13,B14:B14,D14:M14,B15:M22; Exhibit 9 A1:P30 -> A1:P22,A23:M23,A24:P30. Same range text in graderGuidance. Checked with the real scorer (font_color mode): new golden 1.0; input + all 21 key colour changes 1.0; that plus green on the excluded DCF/WACC cells and a repaired Exhibit 9 row 23 still 1.0; untouched input fails.
- other finding, major, not in findings.json: Prompt asks for a full audit-and-fix, but the grader checks only selected font colours and penalises other legitimate fixes
  - Change: answer_position: Exhibit 9!N23:P23 left out (no single defensible replacement for the lost #REF! reference), so a repair is not penalised; part of the same answer_position change as another finding (not listed). Checked with the real scorer (font_color mode): new golden 1.0; input + all 21 key colour changes 1.0; that plus green on the excluded DCF/WACC cells and a repaired Exhibit 9 row 23 still 1.0; untouched input fails.
