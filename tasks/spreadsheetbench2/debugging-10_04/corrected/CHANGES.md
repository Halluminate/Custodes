# Changes: SpreadsheetBench 2 debugging-10_04

Fix summary (from the fix record):

Two defects: the circular revolver loop makes the golden fail its own forced recalculation, and the prompt's three-color rule contradicts the answer key's recolors. The unstable loop cells are dropped from answer_position, and one prompt sentence now states the four-color convention the key uses.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_10_golden.xlsx

## Fixed

- [F8](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells trivially fails (even on gt_10_golden.xlsx) and reports uninformative error messages in font_color mode
  - Change: verifications[0].parameters.answer_position: the 'Model' and 'P&L Summary' ranges are split into runs that skip 187 cells whose values depend on the iterative revolver/interest loop (Model I:M rows 121-124, 126-127, 141, 146-147, 180-183, 186-190, 193-199 (revolver/interest loop), Model R:T and AL:AN rows 24-25, 27-28, 30-31, Model AW20:AW23, AW37, AW39:AW41, Model X20 and X26 (TEXT multiples of the loop), and 'P&L Summary' G40:K41 and R7:T8). Model!I195 references ending cash I$182, which already contains I195, so LibreOffice's iteration oscillates and the result depends on the starting cache. The cell set is the union of cells that missed the golden's cached values in four starting states (golden recalculated once and twice, re-recalculated, and re-saved without caches). All other ranges are unchanged. grader_guidance.md range note updated. Locally (before: golden scored modification 0.1814, 251 errors), the golden, the golden re-saved without caches, and the golden recalculated once and twice all score regression 1.0, modification 1.0. The 84 remaining regression misses are 4-Wall Analysis line-break text cells, within the 0.2% regression allowance. The uninformative font_color error message is verifier code and is not changed.
- [F7](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: Same answer_position change. Locally (before: golden scored modification 0.1814, 251 errors), the golden, the golden re-saved without caches, and the golden recalculated once and twice all score regression 1.0, modification 1.0. The 84 remaining regression misses are 4-Wall Analysis line-break text cells, within the 0.2% regression allowance.
- [F4](../findings.json) (Reward): Ground truth workbook contains unconverged circular-reference cached values causing 186 spurious modification cells that fail LibreOffice recalculation
  - Change: Same answer_position change: the circular-schedule cells whose cached values cannot be reproduced are no longer compared.
- [F6](../findings.json) (Reward): Ground truth fails its own verifier: submitting the golden file scores 0
  - Change: Same answer_position change. Locally (before: golden scored modification 0.1814, 251 errors), the golden, the golden re-saved without caches, and the golden recalculated once and twice all score regression 1.0, modification 1.0. The 84 remaining regression misses are 4-Wall Analysis line-break text cells, within the 0.2% regression allowance.
- [F2](../findings.json) (Reward): Nonconverged golden calculation caches fail the verifier's own recalculation
  - Change: Same answer_position change. Locally (before: golden scored modification 0.1814, 251 errors), the golden, the golden re-saved without caches, and the golden recalculated once and twice all score regression 1.0, modification 1.0. The 84 remaining regression misses are 4-Wall Analysis line-break text cells, within the 0.2% regression allowance.
- [F3](../findings.json) (Style): Undisclosed four-color font convention (purple for intra-sheet links vs green for cross-sheet links) and unflagged operator exceptions in ground truth
  - Change: prompt.md: replaced the convention sentence 'This model uses a three-color font convention: black for formulas that include operators or functions, green for pure cell references (same-sheet or cross-sheet), and blue for hardcoded input values.' with 'This model uses a four-color font convention: blue for hardcoded input values, green for links to other sheets (including links that are only sign-flipped or divided by Mil), purple for links to cells on the same sheet (including sign-flipped ones), and black for all other formulas.' This is the convention the answer key and the rest of the workbook use: GT recolors C52:F52 and D56:F56 (='FY…'!O17/Mil, =-'FY…'!O21/Mil) to green 00B050 and H150 (=G150), I125 (=I131), I130 (=I119) to purple 7030A0, and the Model sheet holds 162 green /Mil cross-sheet links and 224 purple same-sheet links. All 18 GT color changes now follow the stated rule.
- [F1](../findings.json) (Style): Ground-truth recolors contradict the font convention the prompt states
  - Change: Same prompt sentence change as F3.
- [F5](../findings.json) (Style): Golden font colors contradict the explicitly required three-color convention
  - Change: Same prompt sentence change as F3.
- other finding, major, not in findings.json: Prompt asks for a thorough audit, but the GT leaves thousands of convention violations and broken references in place
  - Change: gt_10_golden.xlsx font colours only (XML level, cloned font/xf entries; values, formulas and all other styles unchanged): every graded hardcoded number in black 000000 (43,312 cells, mostly the FY statement sheets) and the Rollup inputs in 99A8BD/4472C4 (43 cells) -> blue 0000FF, the model's input blue; the operator formulas Model!D15, D16, C131:F131 (green) and Rollup!C52 (70AD47) -> black. answer_position: the 34 cells whose formulas contain #REF! (Model!D2, 'FY2024A (Earnings)'!C5:N5, 'FY2027P (IS)'!K33:N33, 'FY2027P (Earnings)'!A1, 'FY2028P (IS)'!A3:A4, C9, L9, C33:N33) are left out, since the deleted targets cannot be recovered, so there is no single repair; grader guidance range text updated. Not changed: Rollup!C63:H65 (=Model!x*1000000, a unit-scaled link, green is defensible under the stated rule). Checked with the real SB2 scorer (font_color mode, forced LibreOffice recalc, new answer_position): new key vs itself PASS (reg 1.0, mod 1.0) and input plus the 26 planted colour fixes plus these recolours PASS (the 84 remaining regression misses are the pre-existing 4-Wall Analysis line-break text cells, within the 0.2% allowance); untouched input FAIL (mod 0.0); old key FAIL.
