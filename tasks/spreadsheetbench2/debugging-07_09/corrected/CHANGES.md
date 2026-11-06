# Changes: SpreadsheetBench 2 debugging-07_09

Fix summary (from the fix record):

The golden cached unconverged values for the circular LBO debt schedule, and LibreOffice's iteration lands on different values depending on the saved caches, so even the golden failed. The golden now caches the converged values, and the untouched circular block T46:X59 is dropped from answer_position. The golden and an openpyxl-saved copy of it both pass the real verifier. The key now also corrects the model errors QA named (Equity Returns Scenario 2 column-D anchors and literal-1 preference formulas, DCF inventory link to P&E, Margin Analysis x1000 revenue total).

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_07_golden.xlsx

## Fixed

- [F5](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells trivially fails (scores 0.0 even on gt_07_golden.xlsx itself and on converged golden solutions)
  - Change: gt_07_golden.xlsx 'LBO & Lenders': cached values of the 38 formula cells in the circular debt schedule and its dependents (T50:X59 rows 49-51/53/57-59, X46, X47, R62, R63) replaced with the fully converged values (LibreOffice recalculated to a fixed point, matching the closed-form solution, e.g. X53 109.638 -> 114.393, X50 -16.826 -> -12.072); formulas and all other cells unchanged (XML <v> edit). Verifier parameter answer_position: "'LBO & Lenders'!B2:Z65" split into B2:S65, T2:X45, T60:X65, Y2:Z65, dropping only T46:X59, the circular interest/debt block whose formulas are identical in input and golden and whose values depend on where LibreOffice's iteration starts (an openpyxl-saved correct output recalculates to X50 -14.61 vs converged -12.07). Same range change in grader_guidance.md. Local grade: new golden, openpyxl-saved golden and the old golden all score reg 1.0 / mod 1.0 (openpyxl-saved scored mod 0.5769 with 30 errors before).
- [F4](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: Same GT converged-cache edit plus the T46:X59 exclusion; golden scores 1.0.
- [F3](../findings.json) (Reward): Ground truth gt_07_golden.xlsx stores unconverged circular-reference values in LBO & Lenders!T49:X59 and fails its own verifier
  - Change: Same GT converged-cache edit (X53 now satisfies =X54*AVERAGE(X49,X51)) plus the T46:X59 exclusion.
- [F2](../findings.json) (Reward): The ground truth fails its own grading: circular LBO debt schedule recalculates to different values in LibreOffice
  - Change: Same GT converged-cache edit plus the T46:X59 exclusion.
- [F1](../findings.json) (Reward): The golden workbook fails its own recalculated cell check
  - Change: Same GT converged-cache edit plus the T46:X59 exclusion.
- other finding, major, not in findings.json: Broad audit prompt conflicts with ground truth that leaves multiple broken references and formula bugs in graded ranges unfixed
  - Change: gt_07_golden.xlsx (built on the critical-pass key, XML-level edits, every other cell/style unchanged): Equity Returns Scenario 2 anchors moved from Scenario 1's column D to column I: H63 =I34/SUM($I$34:$I$36), H70:I70 RATE(...,-$I$36,...), H75:I75 IF($I$60*...), H86:I86 RATE(...,-$I$35,...); preference formulas I57 =I56*(1+$D$12)^$D$10-I56 and H82:I82 =H81*(1+$D$12)^$D$10-H81 (mirror D57/C82; -660,464 -> -210,963); DCF Model D85:F85 Inventory ='BS & CF'!E9:G9 (480/534/568, was P&E row 10); Margin Analysis C25:E25 =SUM(C22:C24) etc. without the *1000 (6,394,000 not 6,394,000,000). Cached values updated only for the 128 cells these edits move (the 16 edited cells plus their dependents on DCF Model, Football Field E5:G5, Equity Returns, LBO & Lenders rows 43/44/47 and R62:R63), taken from the SB2 LibreOffice recalc and confirmed a fixed point by a second recalc. answer_position unchanged (the circular T46:X59 block was already excluded and is not moved). SB2 scorer: new key 1.0/1.0; untouched input plus the key's formula changes 1.0/1.0; untouched input mod 0.0 (130 errors); critical-pass key now mod 0.115, as intended. Prompt unchanged.
- other finding, major, not in findings.json: The answer key preserves material errors that the requested thorough audit should repair
  - Change: Same answer-key correction as another finding (not listed) (DCF D85:F85 now read inventory, Margin Analysis E25 = 6,394,000, Equity Returns I57 = -210,962.97).
