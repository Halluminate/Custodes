# Changes: FINCH task-125

Fix summary (from the fix record):

Reference text corrected for the bondholder outflow (-0.43 not ~-1), guidance accepts a dollar or percent 2023 increase, and the GT now includes the reference text as gt_answer.txt.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_answer.txt (new file)

## Fixed

- other finding, minor, not in findings.json: The reference answer overstates the cumulative bondholder net outflow
  - Change: graderGuidance reference text: '“Commercial bank and other” and “Bondholders” together show small net outflows of around US$1 billion each' -> 'show small net outflows of around US$1.2 billion and US$0.4 billion respectively' (recomputed from U8:W9: -1.230 and -0.427). Same sentence in the new gt_answer.txt.
- other finding, minor, not in findings.json: The grader's reference overstates cumulative bondholder net outflows
  - Change: Same reference-text correction as another finding (not listed).
- other finding, major, not in findings.json: 'Increase in net transfers' is ambiguous (dollar change or percent), and the pass/fail grader only knows the percent
  - Change: graderGuidance: one task-note sentence after the reference text accepting the 2023 increase as a dollar change (about US$5.42 billion) or as a percentage (24.8%).
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Added ground-truth file gt_answer.txt holding the guidance's reference answer text (as corrected under another finding (not listed)), so the staged reference carries the required written analysis next to gt_125_ref_0.xlsx. NOTE: this is a NEW ground-truth file (ground_truth had only gt_125_ref_0.xlsx); applying it needs the editor patch, an upload alone does not reach runs.
