# Changes: SpreadsheetBench 2 debugging-01_07

Fix summary (from the fix record):

Recalculated gt_01_golden.xlsx with the grader's own LibreOffice pipeline, which clears the stale TABLE-polluted caches (C11, C32, C34, C37, U41, U43 and others), and removed the 100 data-table grid cells 'Ex 1 - LBO'!AG18:AK49 from answer_position. The 7 INDEX/MATCH fixes are graded as before. Full pass: the Ex 5 downside cohort cells whose upside-count references the golden keeps are no longer graded, so repairing them does not fail a correct output.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_01_golden.xlsx

## Fixed

- [F5](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells fails all units (score=0) because freeze_datatable_formulas during grading diverges from the TABLE-polluted cached values in gt_01_golden.xlsx
  - Change: gt_01_golden.xlsx: the 65 stale cached values are rewritten at XML level to the verifier's LibreOffice recalculation (C11=14.2034, C32=101.3452 etc.); formulas, TABLE() grids and styles are unchanged. verifications[0].parameters.answer_position: 'Ex 1 - LBO'!B1:AK95 split to skip the TABLE() grid cells AG18:AK22, AG27:AK31, AG36:AK40, AG45:AK49 (100 cells, cached '2.4x/19%'). Checked locally: the input with only the 7 golden INDEX/MATCH formulas applied with openpyxl scores 1.0, the original golden (cached and openpyxl-saved) scores 1.0, the untouched input scores 0.
- [F4](../findings.json) (Verification): Golden gate: the ground-truth deliverable does not score full reward
  - Change: Same: the golden now scores 1.0 on the cell check (was 0.0 with 65 errors).
- [F1](../findings.json) (Verification): Golden workbook (gt_01_golden.xlsx) contains corrupted LibreOffice Multiple Operations cached values and fails its own verifier
  - Change: Corrupted Multiple Operations caches replaced by the recalculated golden, and the grid cells are no longer graded.
- [F2](../findings.json) (Verification): The ground-truth workbook fails its own verifier, so no output can pass
  - Change: Same golden recalculation: C32, U41 and other stale caches now match their formulas.
- [F3](../findings.json) (Verification): Stale golden-workbook values cause the expected solution to fail grading
  - Change: Same golden recalculation plus answer_position grid exclusion.
- other finding, major, not in findings.json: Answer key preserves phantom acquisition EBITDA and penalizes its repair
  - Change: verifications[0].parameters.answer_position: 'Ex 5 - M&A'!B1:AB81 split to skip E58:G62 and Z58:AB63, the downside and active-case 2028-2030 cohort EBITDA, its totals and the row-63 cells AA63:AB63 that read them. In the golden, Z58:AB58, AA59:AB59 and AB60 point at the upside counts $S33/$T33/$U33. The golden is left as is. graderGuidance range list updated. Checked with the real scorer: golden with those six formulas repointed to $Z33/$AA33/$AB33 FAIL before (reg 0.9976, 20 errors), PASS after; golden PASS; input plus the 7 golden formula changes PASS; untouched input FAIL (mod 0.0307).
