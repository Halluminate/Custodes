# Changes: SpreadsheetBench 2 debugging-01_02

Fix summary (from the fix record):

TABLE() data-table cells and a CSE array formula could not survive the verifier's forced recalculation, so even the GT scored 0. Converted them in the GT and reference copy to the form the recalculation produces. The C7 multiple-expansion key is left as is (see notFixed). Full pass: the key now also fixes the further QA-named errors with one defensible correction (11 cells), and named errors without one are left out of answer_position.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_01_golden.xlsx
- reference/untouched_input_Embedded Hardcode_input.xlsx

## Fixed

- [F5](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: files/gt/gt_01_golden.xlsx and files/gt/untouched_input_Embedded Hardcode_input.xlsx (the verifier's reference_path copy): replaced the 100 TABLE() cells in 'Ex 1 - LBO'!AG18:AK22, AG27:AK31, AG36:AK40, AG45:AK49 with their cached text values (e.g. '2.4x/19%'), which is exactly what the verifier's freeze_datatable_formulas leaves in a recalculated output. Rewrote the CSE formula 'Ex 1 - LBO'!C36 from 'Ex 10 - Balance Sheet'!D8:D8/C7 to the array formula 'Ex 10 - Balance Sheet'!D8/C7 that LibreOffice writes back. Same edits in both files, so these stay regression cells. No other cell changed. Local check (formula mode): patched GT scores PASS against itself, and input + all GT formula fixes scores PASS
- [F6](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells always scores 0.0 in formula mode on workbooks containing TABLE() data tables and CSE formulas due to destructive preprocessing in recalculate_xlsx
  - Change: files/gt/gt_01_golden.xlsx and files/gt/untouched_input_Embedded Hardcode_input.xlsx (the verifier's reference_path copy): replaced the 100 TABLE() cells in 'Ex 1 - LBO'!AG18:AK22, AG27:AK31, AG36:AK40, AG45:AK49 with their cached text values (e.g. '2.4x/19%'), which is exactly what the verifier's freeze_datatable_formulas leaves in a recalculated output. Rewrote the CSE formula 'Ex 1 - LBO'!C36 from 'Ex 10 - Balance Sheet'!D8:D8/C7 to the array formula 'Ex 10 - Balance Sheet'!D8/C7 that LibreOffice writes back. Same edits in both files, so these stay regression cells. No other cell changed. Local check (formula mode): patched GT scores PASS against itself, and input + all GT formula fixes scores PASS
- [F4](../findings.json) (Reward): Grader recalculation pipeline freezes TABLE() data-table formulas and collapses array formulas before formula-mode comparison, causing even the golden file to fail
  - Change: files/gt/gt_01_golden.xlsx and files/gt/untouched_input_Embedded Hardcode_input.xlsx (the verifier's reference_path copy): replaced the 100 TABLE() cells in 'Ex 1 - LBO'!AG18:AK22, AG27:AK31, AG36:AK40, AG45:AK49 with their cached text values (e.g. '2.4x/19%'), which is exactly what the verifier's freeze_datatable_formulas leaves in a recalculated output. Rewrote the CSE formula 'Ex 1 - LBO'!C36 from 'Ex 10 - Balance Sheet'!D8:D8/C7 to the array formula 'Ex 10 - Balance Sheet'!D8/C7 that LibreOffice writes back. Same edits in both files, so these stay regression cells. No other cell changed. Local check (formula mode): patched GT scores PASS against itself, and input + all GT formula fixes scores PASS
- other finding, major, not in findings.json: Broad audit prompt instructs agent to fix formula logic errors, #DIV/0! errors, and naming/best-practice issues that the golden solution leaves untouched and penalizes as regression errors
  - Change: gt_01_golden.xlsx (built on the critical-pass key; XML edits, only these cells changed, cached values of the edited cells kept or set to their direct result, no recalculation of other cells): 'Ex 1 - LBO'!X21 =Q89 -> =P89 (the 2025A column, Y21:AB21 use Q:T); C41 '...I8/1000' -> '...I8/$C$7' and P37 '.../1000' -> '.../$C$7' (C7 is the Units Converter, 1000); O89 'Cash Flow Avaliable After PIK Payment' -> 'Available'; W25 'Equity Contributed for Add-On Acquistions' -> 'Acquisitions'; 'Ex 5 - M&A'!Z58:AB58 $S33 -> $Z33, AA59:AB59 $T33 -> $AA33, AB60 $U33 -> $AB33 (Downside cohorts now use Downside acquisition counts like Z48). verifications[0].parameters.answer_position (id/name/function/weight unchanged; graderGuidance range list updated): named errors with no single defensible correction are no longer compared: 'Ex 5 - M&A'!E43:G43, D53:G53, D63:G63, D73:G73 (#DIV/0! at C4=3; any IFERROR fallback is a choice), Y53:AB53, Y63:AB63, Y73:AB73 ('% Margin' computing growth; '=Y52/Y42' and the IFERROR-wrapped form are both defensible under exact formula-text grading), 'Ex 1 - LBO'!I19:M20, I24:M25, I29:M30 (Upside/Downside rows identical to Base; restoring them needs scenario data the file does not hold), O80 (TLB-block label, several valid wordings), AC21 (=AB21+U89 vs per-year =U89 depends on whether cash accumulates, which the model leaves open). Local SB2 grade (formula mode, new ranges): patched GT 1.0/1.0; reference copy + all key changes (planted 17 + these 11) 1.0/1.0; untouched reference mod 0.0; the previous key now fails on exactly the 11 new cells.
- other finding, major, not in findings.json: 'Audit and fix thoroughly' ask conflicts with grading that penalizes fixing anything except the planted hardcodes (output_scope_mismatch / contradictory_requirements)
  - Change: Same key edits (X21, O89, W25) and exclusions (case rows, AC21) as another finding (not listed).
- other finding, minor, not in findings.json: Model scenario rows are identical, so the Operating Case switch does nothing
  - Change: 'Ex 1 - LBO'!I19:M20, I24:M25, I29:M30 left out of answer_position (same change as another finding (not listed)); no single defensible scenario values exist in the file.

## Confirmed findings not fixed

- [F1](../findings.json): Mandatory recalculation makes the golden workbook fail its own verifier
  - Reason: duplicate-of:F4
- [F2](../findings.json): Answer key's 'Multiple Expansion' formula multiplies the change in multiple by the multiple, not by exit EBITDA
  - Reason: cannot-fix-safely: formula-mode grading accepts one formula text only. The input's planted hardcode '*14.2' is the exit multiple, so the benchmark's intended fix is *'Ex 1 - LBO'!AC18. Switching the key to the financially correct *AC17 would fail that intended fix and change what the task tests, and values mode cannot tell the two apart (C7 = 0 either way) while it would also stop checking every hardcode fix
- [F3](../findings.json): Required answer formula miscalculates the multiple-expansion value bridge
  - Reason: duplicate-of:F2
