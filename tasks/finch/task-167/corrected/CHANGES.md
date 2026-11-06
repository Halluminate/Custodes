# Changes: FINCH task-167

Fix summary (from the fix record):

The answer key depended on a 90/10 PA & KH / CIS split and a $13,000,000 sale value that appear nowhere in the inputs, and it dropped CIS's Year-3 distribution and left O14:O16 blank so the CIS NPV skipped three periods. One prompt sentence now states the split and sale value, the key fills O14:O16, and the guidance accepts either sign for the priority shortfall. Full pass: the guidance accepts either NPV timing for the Year 1 outlay.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- reference/gt_167_ref_0.xlsx

## Fixed

- [F2](../findings.json) (Environment & Infra): Ground truth relies on undisclosed 90%/10% partner split, undisclosed $13,000,000 exit valuation in Row 26, and unstated shortfall sign convention
  - Change: prompt.md: added one sentence after 'populate the capital stack and return analysis as shown.' giving the 90%/10% split of cash after the priority return and the Year-13 reversion of a $13,000,000 sale less the permanent loan split the same way. grader_guidance.md: added one sentence accepting either sign for the shortfall in Cash after priority / Unfunded priority if it carries forward the same way.
- [F6](../findings.json) (Verification): Ground-truth workbook (`gt_167_ref_0.xlsx`) omits Year 3 CIS cash flow (`O16`) and leaves `O14:O16` blank, causing Excel `NPV` in `O28` to mis-discount CIS cash flows by 3 years
  - Change: gt_167_ref_0.xlsx 'version 1': O14 =M14 (0), O15 =M15 (0), O16 =M16 (1,304.30), formatted like O17; O28 cached value 132,398.74 -> 68,455.96 (the formula is unchanged, now discounting each CIS flow in its own year). Everything else is identical, and a LibreOffice recalc reproduces the cached values.
- [F3](../findings.json) (Task Spec): The answer key depends on deal terms that appear nowhere in the materials (90/10 split, $13M exit value, timing of CIS cash flows)
  - Change: Same prompt sentence (90/10 split, $13M sale less permanent loan after Year 12) and the same GT patch for the CIS timing. The 15% in I10 sits under the existing 'Cumulative Priority Return' header and the 1.6M Year-2 equity return follows from C15 in the source, so neither needs a change.
- [F4](../findings.json) (Verification): In the GT, CIS's year-3 share is deducted from PA & KH but never paid to CIS, so the partner cash flows don't add up
  - Change: Same GT patch: O16 now pays CIS the 1,304.30 deducted in N16, so N16+O16 = H16.
- [F5](../findings.json) (Environment & Infra): Required distribution and exit assumptions are missing from the task inputs
  - Change: Same prompt sentence supplying the distribution split and exit value.
- [F1](../findings.json) (Verification): Reference CIS cash flows omit a distribution and produce an inflated NPV
  - Change: Same GT patch; O28 is now 68,455.96.
- other finding, major, not in findings.json: The GT NPV discounts the year-1 equity outlay by a full period
  - Change: graderGuidance: one sentence added after the shortfall-sign sentence: 'NPV@25 may discount the Year 1 equity outlay by one period, as the reference does with =NPV(0.25, Year 1 through the reversion row), or treat it as an undiscounted time-0 flow; either timing is correct.' Key unchanged.
