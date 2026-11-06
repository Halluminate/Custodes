# Changes: SpreadsheetBench 2 debugging-01_01

Fix summary (from the fix record):

The answer key and its untouched-input reference held 65 stale LibreOffice multiple-operations caches, so even the golden workbook failed. In both files those cached values are now the verifier's own recalculated values (formulas and data tables untouched), and the four Ex 1 data-table grids, whose frozen caches test the save engine rather than the fix, are left out of the compared range. Golden and a plain openpyxl fix now pass; the untouched input still fails. Full pass: the Downside cohort EBITDA in Ex 5 (Z58:AB60) referenced the Upside acquisition counts, so the key required phantom EBITDA (F62 21.528, G62 37.03); the golden now uses the Downside counts (all 0). Side effect: with Downside totals all 0, the planted Ex 5 cumulative add-back no longer changes any value, so Ex 1 AC20 plus this cohort fix carry the grading.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_01_golden.xlsx
- reference/untouched_input_Double Counting_input.xlsx

## Fixed

- [F5](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: ground_truth/gt_01_golden.xlsx and untouched_input_Double Counting_input.xlsx: cached <v> of the 65 stale formula cells (Ex 1 34, Ex 2 3, Ex 5 28, e.g. 'Ex 1 - LBO'!C11 18.2034 -> 14.2034, C32 109.5182 -> 101.3452) replaced with the values from the verifier's own managed_recalculated_xlsx; no formula, style or other cell changed. answer_position now skips the TABLE() grids. Local replay: golden PASS (reg 1.0, mod 1.0).
- [F6](../findings.json) (Verification): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells trivially fails (score 0.0) on all runs and on the golden workbook itself due to asymmetric LibreOffice recalculation
  - Change: Same recalculated GT/reference (no stale caches such as C11 18.2034 or C32 109.5182 left) plus the data-table cells removed from answer_position; an openpyxl output with only the 22 GT formula fixes now scores PASS, the untouched input scores mod 0.0.
- [F2](../findings.json) (Verification): Ground truth workbook gt_01_golden.xlsx contains corrupted LibreOffice data-table cache values and fails its own verifier
  - Change: Same: GT recalculated so its caches match its formulas (F22 sources = F28 uses), flat '2.4x/19%' data-table interiors no longer graded. The Ex 5 fixes still evaluate to 0 under Case 3, which is the benchmark's design and was not changed.
- [F1](../findings.json) (Verification): The ground-truth workbook's stale, self-contradictory cached values make it fail its own verifier, so no output can pass
  - Change: Same GT/reference recalculation; golden self-check now passes.
- [F4](../findings.json) (Verification): The sensitivity table in the GT is flat, so 100 graded cells all hold the same string
  - Change: verifications[0].parameters.answer_position: 'Ex 1 - LBO'!B1:AK95 split into B1:AF95, AG1:AK17, AG23:AK26, AG32:AK35, AG41:AK44, AG50:AK95 so the 100 TABLE() cells (AG18:AK22, AG27:AK31, AG36:AK40, AG45:AK49) are not compared; the AF17/AF26/AF35/AF44 corner labels that move with the fix stay graded.
- [F3](../findings.json) (Verification): Stale golden-workbook values cause the golden solution itself to fail grading
  - Change: Same GT/reference recalculation; golden replay passes.
- other finding, major, not in findings.json: Answer key requires phantom acquisition EBITDA from the wrong scenario
  - Change: gt_01_golden.xlsx (sheet5.xml edited at the XML level, every other cell and file byte unchanged): 'Ex 5 - M&A' Downside 2028-2030 cohort EBITDA Z58:AB58 now use $Z33, AA59:AB59 $AA33, AB60 $AB33 (were the Upside counts $S33/$T33/$U33), matching the Downside revenue/GP/synergy cohort rows 38-40, 48-50, 68-70. Cached values written: Z58:AB58, AA59:AB59, AB60, E58:G58, F59:G59, G60, E62:G62, Z62:AB62 = 0 (Downside has 0 acquisitions) and AA63:AB63 = 'N/A' (IFERROR of 0/0). Real SB2 scorer (answer_position unchanged): golden 1.0; plain openpyxl output with the 22 keyed fixes plus this fix 1.0; same plus margin rows as Y52/Y42, IFERROR on D:G 43/53/63/73, X26 =X23 and Ex 2 C7 *AC17 still passes (reg errors only #DIV/0! vs N/A, within the allowance); the 22 keyed fixes without this one now fail (Ex 5 E58:G62); untouched input mod 0.0. Ex 5 C4 hardcoded case 3 was left as is: an independent M&A case selector next to Ex 1's separate M&A switch is a valid design, not a single defensible correction. X26, Ex 2 C7, Ex 1 C36 and the F63 #DIV/0! are value-neutral; C33 is a share-count input.
- other finding, major, not in findings.json: Generic audit instruction and false Python environment claim mislead agents into ungraded or penalized edits
  - Change: Same Ex 5 Z58:AB60 answer-key correction as another finding (not listed) (the named Case 3 cross-reference). The other named items need no key change: X26 double-count and the Downside % Margin rows are value-neutral once the cohort fix is in (X25 = 0, all Downside totals 0); C4 = 3 is a valid independent case input. The Python-environment half is infra.
