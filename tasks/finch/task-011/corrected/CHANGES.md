# Changes: FINCH task-011

Fix summary (from the fix record):

No change. The only true finding is the excel_read_range tool recomputing in LibreOffice and returning Err:502 for Excel-valid OFFSET formulas instead of the stored values; that is tool behaviour, and rewriting the input formulas would change the task. Full pass: the reference NAV chart now has annual ticks and direct series ranges covering every row, so it renders dated X-axis labels.

Changed files (in this folder):

- reference/gt_11_ref_0.xlsx

## Fixed

- other finding, major, not in findings.json: Ground-truth chart in gt_11_ref_0.xlsx omits annual time-axis tick settings, uses legacy Chinese defined names that drop the final data row (2025-11-05), and renders no X-axis labels in LibreOffice
  - Change: files/gt/gt_11_ref_0.xlsx, xl/charts/chart1.xml only (XML edit, every other part byte-identical): the date axis gets <c:majorUnit val="1"/><c:majorTimeUnit val="years"/> (annual ticks, as the task requires); the three series references [0]!时间/[0]!净值/[0]!基准 (OFFSET names that LibreOffice renders with no X-axis labels and that stop at 2025-11-04) become Timing_Strategy!$A$14:$A$5075, $M$14:$M$5075, $N$14:$N$5075, with the 2025-11-05 point (45966, 11.676430147106053, 5.902145535671254) added to each cache (ptCount 5061 -> 5062). Colours, markers, placement and workbook cells unchanged. LibreOffice PDF of the key now shows yearly X-axis labels (2005-12-31 ... ) where the original showed none.
- other finding, major, not in findings.json: The ground-truth chart does not have the annual time-axis ticks the task requires
  - Change: Same chart1.xml edit (annual majorUnit/majorTimeUnit on the date axis).
- other finding, major, not in findings.json: NAV named ranges omit the final observation
  - Change: Same chart1.xml edit: the key's series now cover all 5,062 rows through 2025-11-05. The input's O2 formula and names are left as is (input files unchanged).
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Same chart1.xml edit, which removes the verified cause of the low GT grade (no annual ticks, no visible X-axis). Not re-run through the guidance test locally.
