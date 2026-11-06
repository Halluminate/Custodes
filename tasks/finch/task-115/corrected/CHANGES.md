# Changes: FINCH task-115

Fix summary (from the fix record):

Added one task-specific note to the grader guidance so answers built on any official HPI vintage are accepted and the derived sheets are checked against the model's own RawData, instead of failing for not matching the reference's spliced vintage within 1%.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- [F1](../findings.json) (Reward): The grader accepts data from any publication date but only tolerates 1% difference from one reference, so valid answers are rejected
  - Change: grader_guidance.md: added one note after the web-search tolerance note: accept RawData values matching any official HM Land Registry/ONS publication for that month, and judge Sheet2-Sheet5 by correct computation from the model's own RawData rather than closeness to the reference.
- [F3](../findings.json) (Reward): Grading tolerance conflicts with explicitly permitted HPI publication vintages
  - Change: Same added guidance note; a consistently sourced later vintage is no longer failed by the 1% band against the reference.
- [F2](../findings.json) (Verification): The reference RawData joins pre-revision and post-revision UK HPI data, and the grader compares to it within 1%
  - Change: Same added guidance note; the reference's spliced pre/post-revision RawData and its derived MoM, max/min and category values are no longer the pass/fail target, so a single consistent official series is graded on its own correctness.
