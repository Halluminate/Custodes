# Changes: FINCH task-090

Fix summary (from the fix record):

The answer key carried over unrelated original formatting (header underlines, lines on empty cells, lines a row or two above the totals) and so contradicted the one-line instruction. Its Summary borders now match the source except for a thin top border on each value that is a sum of the rows above it. Full pass: grader guidance now lists the key cells and accepts either choice on five borderline cells (G10, G41, E66, F66, C46), since the formula-free sheet makes them a judgment call.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_90_ref_0.xlsx

## Fixed

- [F2](../findings.json) (Style): Ground-truth workbook gt_90_ref_0.xlsx contradicts the prompt by bordering column headers, empty cells, and wrong rows above blank spacer rows
  - Change: gt_90_ref_0.xlsx Summary: every border that differed from 90_src_0.xlsx reset to the source (removes the C7:Q7 medium and E62:I62 thin header underlines, H46:Q46 top borders on empty cells, Q51, G65:I65, E70:I70 and the bottom borders above sum rows; source A7:B7 header borders kept), then a thin top border added to the row-sum values F10 G10 F13 G13 C17 F21 G21 F24 G24 F30 G30 F33 G33 F41 G41 H47 I47 K47 L47 N47 O47 Q47 Q54 E66 F66 E72 F72 H72 I72. No values or other sheets changed.
- [F1](../findings.json) (Style): The ground truth adds borders the instruction does not ask for: header underlines and lines on empty cells
  - Change: Same GT patch: no header underlines or borders on empty cells remain, so a minimal correct answer matches the key.
- other finding, critical, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Same GT patch: the key no longer over-edits, which was why it graded 0.70-0.82 under its own rubric.
- other finding, major, not in findings.json: Ambiguous definition of 'values calculated as the sum of other rows' on a formula-stripped Summary sheet
  - Change: graderGuidance: added a task-specific note listing the reference top-bordered cells (from the patched key) and accepting either choice on the borderline cells G10, G41, E66, F66 and C46; a bottom border on the cell above counts as the same line. Official judge text kept verbatim.
- other finding, major, not in findings.json: The workbook has no formulas, so 'calculated as the sum of other rows' must be worked out by redoing the arithmetic
  - Change: Same graderGuidance note as another finding (not listed).
- other finding, major, not in findings.json: Calculation provenance is absent from the calculation-based formatting task
  - Change: Same graderGuidance note as another finding (not listed).
