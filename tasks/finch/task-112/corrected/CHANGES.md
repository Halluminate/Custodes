# Changes: FINCH task-112

Fix summary (from the fix record):

Full pass: answer key now leaves non-applicable frequency columns blank, as the prompt requires.

Changed files (in this folder):

- reference/gt_112_ref_0.xlsx

## Fixed

- other finding, major, not in findings.json: The prompt says to leave non-applicable columns blank, but the answer key fills them with 0
  - Change: files/gt/gt_112_ref_0.xlsx, weekly sheet XML only: the six IF formulas (masters of M8:O51) '=IF(L8="weekly",K8,0)' etc. -> '=IF(L8="weekly",K8,"")', and the 90 non-applicable cached 0 values in M8:O51 -> empty text, so the key leaves the non-applicable total columns blank as the prompt requires. Sub-totals and Annual Total unchanged (P56 258,640); LibreOffice recalc of the patched key matches every cached value.
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Same answer-key fix as another finding (not listed): the key shown 0 in every non-applicable column against the prompt's explicit "leave blank", the likely cause of the 0.00 self-grade. Not re-probed locally.
