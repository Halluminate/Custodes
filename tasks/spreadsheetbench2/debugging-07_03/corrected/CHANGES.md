# Changes: SpreadsheetBench 2 debugging-07_03

Fix summary (from the fix record):

The circular LBO debt schedule does not settle under the verifier's forced LibreOffice recalculation, so even the golden workbook failed. Those circular cells are dropped from answer_position; the restructured rows and every other cell stay graded. Full pass: the key also fixes the QA-named DCF inventory link, the Margin Analysis x1000 revenue total, the Equity Returns preference return and the 'Automovile' typo.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_07_golden.xlsx

## Fixed

- [F3](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: verifications[0].parameters.answer_position: 'LBO & Lenders'!B2:Z65 split into row runs that skip the circular debt-schedule cells X46:X47, S49:X51, S53:X53, S57:X59 (iterative calc, period-2 oscillation, values depend on the recalculation start point). All other ranges unchanged. Locally: golden and golden re-saved without caches both score 1.0 (before: modification 0.9837, 17 errors); the untouched input still scores 0. grader_guidance.md range note updated to match.
- [F1](../findings.json) (Reward): The ground truth fails its own verifier: circular debt schedule recalculates to different values
  - Change: Same answer_position change as gt-replay-0.
- [F2](../findings.json) (Reward): The golden workbook fails its own mandatory recalculation and grading
  - Change: Same answer_position change as gt-replay-0.
- other finding, major, not in findings.json: The answer key preserves material formula errors that the requested audit should fix
  - Change: gt_07_golden.xlsx (XML-level) now also fixes the QA-named calculation errors: 'DCF Model'!D85:F85 ='BS & CF'!E10/F10/G10 -> E9/F9/G9 (inventory 480/534/568); 'Margin Analysis'!C25:E25 =(SUM(x22:x24))*1000 -> =SUM(x22:x24); 'Equity Returns'!H82:I82 ...^$D$10-1 -> ...^$D$10-H81/-I81 (210,962.97). Cached values from the verifier's LibreOffice recalc injected only for the 117 formula cells these edits move (DCF NWC/FCF/valuation, Football Field E5:G5, LBO S43:X47, Equity Returns rows 82-86, Margin C25:E25); unconverged circular caches untouched. Real SB2 scorer (answer_position from the critical fix): new golden 1.0; golden re-saved without caches 1.0; previous golden 0 (mod 0.894); untouched input 0.
- other finding, major, not in findings.json: Open-ended 'audit thoroughly' prompt asks for more than the ground truth fixes
  - Change: Same file: 'DCF Model'!C57 'Automovile and Travel' -> 'Automobile and Travel' (shared string). The cited hardcodes hold correct values and need no key change under values-mode grading.
