# Changes: SpreadsheetBench 2 debugging-09_08

Fix summary (from the fix record):

The answer key's circular LBO debt and interest cells held cached values from before the loop converged, so even the key failed its own check. Those cached values were replaced with the converged LibreOffice values. Formulas and all other cells are unchanged. Checked locally: the patched key scores 1.0 against itself, and the input with the key's fixes applied scores 1.0 once its own circular loop is converged. Note: an output saved without converged caches (for example openpyxl with no recalculation) still drifts, because the verifier's single LibreOffice pass moves the loop only one step. Full pass: the key's interest-limitation sign fix turned negative limits into add-backs; the key now floors the allowable interest at 0 (G74:K74 = 0) and the limitation/carryforward rows, whose values depend on where the floor is placed, are left out of the compared range. Cleanup pass: the 273 loop cells that do not settle under one LibreOffice recalc are left out of answer_position, so an output saved without cached values also passes.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_09_golden.xlsx

## Fixed

- [F4](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: files/gt/gt_09_golden.xlsx: cached values of 258 cells on the LBO sheet (the circular debt, interest and returns block, e.g. G124, J124, I138, K138, L199:L201, H204, D213) replaced with the converged LibreOffice values (LibreOffice recalculated it 12 times until nothing moved). No formula changed and no other sheet changed.
- [F5](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells fails exact golden-formula solutions (units 2 and 3) with score=0 due to un-converged cached values in gt_09_golden.xlsx
  - Change: Same GT re-cache as gt-replay-0 (converged circular-loop values on LBO).
- [F3](../findings.json) (Reward): Golden workbook (gt_09_golden.xlsx) contains un-converged cached values in its circular LBO debt/interest loop, causing a 100% correct model to fail verification
  - Change: Same GT re-cache as gt-replay-0 (converged circular-loop values on LBO).
- [F2](../findings.json) (Reward): Golden workbook's cached values are stale and do not satisfy its own formulas, so after LibreOffice recalculation the golden fails its own verifier and no output can pass
  - Change: Same GT re-cache as gt-replay-0 (converged circular-loop values on LBO).
- [F1](../findings.json) (Reward): Golden workbook contains inconsistent cached values and fails its own verifier
  - Change: Same GT re-cache as gt-replay-0 (converged circular-loop values on LBO).
- other finding, major, not in findings.json: The sign fix in the golden adds interest to taxable income when the interest limitation is negative
  - Change: files/gt/gt_09_golden.xlsx (on top of the critical re-cache): LBO!G74:N74 formula =-MIN(x81,x82) -> =-MAX(MIN(x81,x82),0); cached G74:K74 23.60/20.01/14.89/9.51/3.68 -> 0 and their only dependents G77:K77 -55.06/-46.70/-34.75/-22.20/-8.58 -> -78.66/-66.71/-49.64/-31.71/-12.25 (L:N values unchanged; taxes in row 79 stay 0). Edited at XML level, nothing else touched. answer_position 'LBO'!A2:X218 -> 'LBO'!A2:X80,'LBO'!A81:F83,'LBO'!O81:X83,'LBO'!A84:X218 so G81:N83 (limitation and carryforward, whose values depend on where the floor is placed) are not compared; graderGuidance range text updated. Local SB2 scorer: patched golden 1.0; input with the key's fixes plus the floor, loop converged, 1.0; untouched input fails; key-fixes-without-floor fails on G74:K74.
- other finding, major, not in findings.json: The prompt asks for a broad audit, but the grader rejects any extra legitimate fix that changes values
  - Change: Same key correction as another finding (not listed) for the named negative-limitation error; the two other named items need no key change (value-preserving).
