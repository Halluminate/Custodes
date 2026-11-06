# Changes: FINCH task-170

Fix summary (from the fix record):

The selected month runs past the end of the source data, and the reference answer handles the missing days with a broken DOW lookup and zero-filled spreads. The AI-judge guidance now tells the judge not to fail other reasonable treatments of those days or blank temperature/gas/heat-rate stats. The guidance also accepts treating New Year's Day 2002 as a NERC holiday, as the Strips comments say, and exact 16/24 and 8/24 strip weights. The reference's Temp!M910:M990 dates are back in date format.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_170_ref_0.xlsx

## Fixed

- [F2](../findings.json) (Verification): Ground truth gt_170_ref_0.xlsx contains corrupted DOW lookups, distorted spread averages from unmasked missing data, and #N/A errors
  - Change: grader_guidance.md: added one task-specific paragraph after the opening paragraph. It tells the judge that Raw Data ends 2002-01-18 and Temp has no January rows, describes the reference's defects (approximate-VLOOKUP DOW 5 for Jan 19-31, no-data and DA-minus-zero days counted as spreads, #N/A temperature/gas/heat-rate cells), and says not to fail outputs that handle missing days another consistent way or leave temperature/gas/heat-rate stats blank or #N/A, while all complete-data cells are still judged against the reference.
- [F1](../findings.json) (Verification): GT spread averages count days with no data as zero-spread weekdays, which changes their sign
  - Change: Same grader_guidance.md paragraph: the judge no longer marks an output wrong for excluding no-data days or using the correct day of week in the spread block.
- [F3](../findings.json) (Environment & Infra): The selected month lacks required fundamental data
  - Change: Same grader_guidance.md paragraph: an output that leaves the temperature, gas and heat-rate statistics blank or #N/A, or applies a stated partial-period convention, is not failed. The missing January data itself cannot be supplied without inventing it.
- other finding, major, not in findings.json: Contradiction between Strips sheet cell comments on NERC Holiday exclusion and gt_170_ref_0.xlsx formulas, plus undisclosed 0.67/0.33 weighting
  - Change: grader_guidance.md: added a task note after the missing-data note. The Strips comments (A45:A49) exclude NERC holidays from the weekday strips and include them in the weekend strips, but the holiday list A74:A97 ends at 2001-12-25 and Raw Data codes 2002-01-01 as DOW 2, so the reference counts New Year's Day as a weekday; the judge now accepts an output that treats 2002-01-01 as a holiday consistently. The note also accepts exact 16/24 and 8/24 weights for Wt 5x24 / Wt 2x24 in place of the reference's 0.67/0.33.
- other finding, major, not in findings.json: Holiday classifications contradict the workbook's averaging specifications
  - Change: Same holiday note as another finding (not listed): an output that follows the comments and treats 2002-01-01 as a NERC holiday is not failed. The 2001 Raw Data misclassifications are outside the selected month and do not affect the graded cells.
- other finding, major, not in findings.json: Prompt gives almost no specification; the answer key depends on design choices the agent cannot infer
  - Change: Same guidance note: exact 16/24 and 8/24 weights for the weighted strips are accepted next to the reference's 0.67/0.33. The other choices named (LMP/DA switch in B60:H60, zone codes in B53:B55, weekday/weekend split by Raw Data DOW) come from the Strips sheet's own parameter cells and headers, so they stay as the reference has them.
- other finding, minor, not in findings.json: Reference workbook changes Temp!M dates into raw serial numbers, outside the task scope
  - Change: gt_170_ref_0.xlsx (XML edit, built on the original reference): Temp!M910:M990 style index 163 (General) -> 2, the mm-dd-yy date style the source and the rest of column M use, so the 81 dates show as dates again (values unchanged). Temp now matches 170_src_0.xlsx cell for cell; no other part changed.
