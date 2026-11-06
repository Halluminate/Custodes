# Changes: FINCH task-110

Fix summary (from the fix record):

The reference stripped the ROUND wrappers from the original Sheet1 the prompt says to preserve, and left the target sheet unrounded against the 4/2-decimal instruction. Restored Sheet1 to the input and applied the instructed rounding in the target sheet's reference formulas.

Changed files (in this folder):

- reference/gt_110_ref_0.xlsx

## Fixed

- other finding, critical, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: files/gt/gt_110_ref_0.xlsx 'Sheet1': restored every cell to the input workbook (ROUND formulas and cached values, e.g. F10 '=ROUND(E10/0.95,4)', O41 1017404.7, Q49 360406.05). Sheet1 is now identical to the input; files/gt/gt_110_ref_0.xlsx "March'01 GDAs": wrapped F10:F40 in ROUND(...,4) and M10:N40, P10:Q40 in ROUND(...,2), mirroring the original Sheet1 so Adj TW Per is 4 dp and profits/splits 2 dp as the prompt asks (H and I follow at 4 dp, O and row 41 at 2 dp). Cached values recomputed in LibreOffice (e.g. F10 5.4632, M10 26622, O41 1018949.27). Both defects the guidance grader could fail the GT on are removed
- other finding, critical, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: same GT fix as exploit-probe-0 (Sheet1 restored, target sheet rounded per prompt)
- [F1](../findings.json) (Verification): Ground truth modifies original Sheet1 by stripping ROUND() formulas, contradicting the explicit instruction to preserve all original sheets and their contents
  - Change: files/gt/gt_110_ref_0.xlsx 'Sheet1': restored every cell to the input workbook (ROUND formulas and cached values, e.g. F10 '=ROUND(E10/0.95,4)', O41 1017404.7, Q49 360406.05). Sheet1 is now identical to the input
- [F2](../findings.json) (Verification): Ground truth changes the original 'Sheet1', even though the prompt says to keep original sheets and their contents
  - Change: files/gt/gt_110_ref_0.xlsx 'Sheet1': restored every cell to the input workbook (ROUND formulas and cached values, e.g. F10 '=ROUND(E10/0.95,4)', O41 1017404.7, Q49 360406.05). Sheet1 is now identical to the input
