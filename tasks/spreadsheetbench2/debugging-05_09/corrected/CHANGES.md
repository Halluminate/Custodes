# Changes: SpreadsheetBench 2 debugging-05_09

Fix summary (from the fix record):

The answer key needs Model!N14 = 8.0% (2030E State & Local Government growth), but the input overwrote that input with a formula and nothing gives the value. One prompt sentence now states the 8.0% assumption. The workbook was not edited because openpyxl cannot load its charts and would drop them. Full pass: the key now also fixes the named Total Current Assets/Liabilities sums (Model E59:N59, E67:N67) and the projection label Model!Q12 ('25E-'30A -> '25E-'30E).

Changed files (in this folder):

- prompt.md
- reference/gt_05_golden.xlsx

## Fixed

- [F1](../findings.json) (Task Spec): Undisclosed hardcoded target growth rate assumption (Model!N14 = 0.08) required by ground truth
  - Change: Added one sentence to the prompt instruction line: 'The 2030E growth assumption for State & Local Government is 8.0%.' This supplies the Model!N14 value the answer key requires (0.08), which the input overwrote with a dragged formula and no file or note states.
- [F3](../findings.json) (Environment & Infra): Graded fix requires a hardcoded 8% terminal growth assumption that was erased from the input and exists nowhere agent-visible (impossible_or_absent_data)
  - Change: Added one sentence to the prompt instruction line: 'The 2030E growth assumption for State & Local Government is 8.0%.' This supplies the Model!N14 value the answer key requires (0.08), which the input overwrote with a dragged formula and no file or note states.
- [F2](../findings.json) (Task Spec): The expected terminal growth assumption is not supplied
  - Change: Added one sentence to the prompt instruction line: 'The 2030E growth assumption for State & Local Government is 8.0%.' This supplies the Model!N14 value the answer key requires (0.08), which the input overwrote with a dragged formula and no file or note states.
- other finding, minor, not in findings.json: Projection-period label marks the 2030 endpoint as actual
  - Change: files/gt/gt_05_golden.xlsx (XML-level edit of the Model sheet only; charts and every other part kept): Model!E59:N59 =SUM(x51:x53,x55,x57) -> =SUM(x51,x53,x55,x57) and E67:N67 =SUM(x61:x63,x65) -> =SUM(x61,x63,x65) (drop row 52 Days Unbilled Outstanding and row 62 Net Revenue % from the dollar totals), and Model!Q12 "'25E-'30A" -> "'25E-'30E". Cached values from the verifier's LibreOffice recalc: only rows 59, 67, 68 and F69:H69 moved (33 cells), as in sibling tasks <id>/<id>/<id>. Real SB2 scorer: new golden 1.0; input + every key change 1.0; input + only the planted fixes 0.0 (mod 0.92); untouched input 0.0.
- other finding, major, not in findings.json: The answer key penalizes correcting non-reconciling balance-sheet totals
  - Change: files/gt/gt_05_golden.xlsx (XML-level edit of the Model sheet only; charts and every other part kept): Model!E59:N59 =SUM(x51:x53,x55,x57) -> =SUM(x51,x53,x55,x57) and E67:N67 =SUM(x61:x63,x65) -> =SUM(x61,x63,x65) (drop row 52 Days Unbilled Outstanding and row 62 Net Revenue % from the dollar totals), and Model!Q12 "'25E-'30A" -> "'25E-'30E". Cached values from the verifier's LibreOffice recalc: only rows 59, 67, 68 and F69:H69 moved (33 cells), as in sibling tasks <id>/<id>/<id>. Real SB2 scorer: new golden 1.0; input + every key change 1.0; input + only the planted fixes 0.0 (mod 0.92); untouched input 0.0.
