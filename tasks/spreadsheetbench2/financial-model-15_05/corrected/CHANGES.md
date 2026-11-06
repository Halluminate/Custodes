# Changes: SpreadsheetBench 2 financial-model-15_05

Fix summary (from the fix record):

Put the 218 IS_BS_CF assumption formulas (rows 142-169) the prompt never asks for back into the input and the untouched reference, and blanked the four unrequested CAGR cells Formats!N4, N5, N7 and N9 in the golden. Now only the Formats and Report Tables work the prompt describes is graded as changes.

Changed files (in this folder):

- reference/gt_15_KIMS_golden.xlsx
- reference/untouched_input_15_05_KIMS_input.xlsx
- inputs/15_05_KIMS_input.xlsx

## Fixed

- [F6](../findings.json) (Task Spec): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check always fails (score 0.0) because untouched_input_15_05_KIMS_input.xlsx and assets/15_05_KIMS_input.xlsx are missing 218 unmentioned formulas in IS_BS_CF!B142:X169
  - Change: Agent input 15_05_KIMS_input.xlsx and reference untouched_input_15_05_KIMS_input.xlsx are now the golden workbook with all 396 Formats/Report Tables task cells blanked, so they contain the 218 IS_BS_CF!B142:X169 formulas and nothing else new. Both were recalculated with the verifier's LibreOffice pipeline. gt_15_KIMS_golden.xlsx: Formats!N4, N5, N7, N9 blanked, then recalculated. Checked locally: the golden scores 1.0 with cached values and after an openpyxl save (no caches), and the untouched input scores 0 (447 modification cells, all in Formats/Report Tables and their links).
- [F1](../findings.json) (Environment & Infra): Input workbook is missing 218 unmentioned historical schedule formulas in IS_BS_CF!B142:X169, causing 1,078 of 1,460 modification cells across 6 sheets to fail
  - Change: Same: IS_BS_CF!B142:X169 formulas restored in both input copies, so the forecast cascade no longer depends on unstated work.
- [F3](../findings.json) (Task Spec): Four undisclosed CAGR scratch formulas in unlabelled column Formats!N4, N5, N7, N9 are graded as modification cells
  - Change: gt_15_KIMS_golden.xlsx Formats!N4, N5, N7, N9 (unlabeled CAGR formulas) blanked, so they are unchanged (regression) cells.
- [F2](../findings.json) (Task Spec): The ratio work is graded in IS_BS_CF's Assumptions block, but the prompt points the agent to the Formats balance sheet
  - Change: The IS_BS_CF Assumptions block is now part of the input, so no graded change sits outside the Formats/Report Tables areas the prompt names.
- [F4](../findings.json) (Task Spec): The GT adds CAGR cells that the prompt never asks for
  - Change: Formats!N4, N5, N7, N9 blanked in the golden.
- [F5](../findings.json) (Environment & Infra): Deleted source formulas and unlabeled calculations exceed the stated task scope
  - Change: Both parts fixed: the 218 formulas are restored in the inputs and the CAGR cells are removed from the golden.
