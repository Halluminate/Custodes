# Changes: SpreadsheetBench 2 debugging-08_05

Fix summary (from the fix record):

The answer key's two NWC averaging windows follow the pattern of the neighbouring rows (earlier fix, kept). The key now also fixes the extra errors QA named: the broken R84 reference, the -30% tax rate in C90 and the '% of revenue' ratios M27/R27 that divided by COGS. The stale hardcoded sensitivity grid G108:K112 has no single correct rebuild and is no longer graded. The earlier scope-limiting prompt sentence is removed, so the prompt is unchanged.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_08_golden.xlsx

## Fixed

- [F5](../findings.json) (Verification): Undisclosed cell-specific historical averaging windows in ground truth (Operating Model + DCF!R72, R81, N18)
  - Change: gt_08_golden.xlsx 'Operating Model + DCF': R72 =AVERAGE(M72,H72,E72:G72) -> =AVERAGE(M72,H72,C72:G72) and R81 =AVERAGE(M81,H81) -> =AVERAGE(M81,H81,C81:G81), the same window R75 and R78 use, which is the only rule the workbook signals. The 61 dependent cached values (rows 71-84 projections, DCF rows 94-145) were recomputed with the verifier's LibreOffice recalculation and written into the original file at XML level, with no other change. Checked locally with the verifier code: input + H12 MEDIAN, N18 0 and the C:G windows scores reg 1.0 / mod 1.0 against the new key; the new key scores 1.0 on itself; the untouched input fails.
- [F1](../findings.json) (Verification): The GT's 'fixes' to the averaging ranges follow no consistent rule, so other reasonable corrections are rejected
  - Change: Same GT R72/R81 re-keying to the C:G window shared by R75/R78 as F5.
- [F4](../findings.json) (Verification): Ground truth retains broken cell reference Operating Model + DCF!R84 (=R847-M83) that the prompt instructs agents to fix
  - Change: files/gt/gt_08_golden.xlsx 'Operating Model + DCF'!R84 '=R847-M83' -> '=R83-M83' (2026 change in NWC, like S84 '=S83-R83'); cached D94, D95, D100, C102, C107:C145 and F107/F121 recomputed with the verifier's LibreOffice recalc and written at XML level. The prompt scope sentence from the earlier fix is removed.
- [F3](../findings.json) (Verification): Golden workbook penalizes correcting a broken working-capital reference
  - Change: files/gt/gt_08_golden.xlsx 'Operating Model + DCF'!R84 '=R847-M83' -> '=R83-M83' (2026 change in NWC, like S84 '=S83-R83'); cached D94, D95, D100, C102, C107:C145 and F107/F121 recomputed with the verifier's LibreOffice recalc and written at XML level. The prompt scope sentence from the earlier fix is removed.
- [F2](../findings.json) (Verification): Answer key leaves obvious errors unfixed (e.g., broken reference R84 '=R847-M83', negative tax rate C90 = -0.3) even though the instruction asks for a thorough audit, so an agent that fixes them fails the all-or-nothing verifier
  - Change: files/gt/gt_08_golden.xlsx 'Operating Model + DCF': R84 -> '=R83-M83', C90 -0.3 -> 0.3 (matches D90:H90), M27 '=M26/M7' -> '=M26/M4' and R27 '=R26/R7' -> '=R26/R4' (the '% of revenue' row divided by COGS; C27:L27 divide by revenue). 27 cached values recomputed (C91 -169.51 -> -91.27, D94 -29.61 -> -144.38, C116 276.80 -> 277.44, M27 -0.0332 -> -0.0057). answer_position: the hardcoded sensitivity grid 'Operating Model + DCF'!G108:K112 is dropped (stale pasted values with no single correct rebuild; its row/column headers stay graded and keep their values if turned into formulas). The prompt scope sentence from the earlier fix is removed.
