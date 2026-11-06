# Changes: FINCH task-067

Fix summary (from the fix record):

Guidance note covering the PG&E Topock area conflict, the #REF! links left by deleting the target sheet, and rep names that differ from the summary.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Input 'area info' worksheet assigns 'PG&E Topock' to 'San Juan', contradicting ground-truth 'by type_area' ('West of Thoreau') and changing 4 area subtotals
  - Change: graderGuidance task note item (1): accepts PG&E Topock under either area, subtotals following.
- other finding, major, not in findings.json: Ground truth puts PG&E Topock in a different area than the workbook's 'area info' mapping
  - Change: graderGuidance task note item (1): accepts PG&E Topock under either area, subtotals following.
- other finding, major, not in findings.json: Deleting 'by type_area' to create 67_src_0.xlsx left #REF! errors in 8 original operator sheets that remain intact in gt_67_ref_0.xlsx and feed GT Column D ('Accum Prod Mo Value')
  - Change: graderGuidance task note item (2): names the nine #REF! links, accepts re-linking them to the agent's index prices (not an over-edit) or leaving them, and accepts the Accum Prod Mo Value column omitted or #REF! in that case.
- other finding, major, not in findings.json: Source workbook has #REF! errors left over from deleting the target sheet, and ground-truth values depend on them
  - Change: graderGuidance task note item (2): names the nine #REF! links, accepts re-linking them to the agent's index prices (not an over-edit) or leaving them, and accepts the Accum Prod Mo Value column omitted or #REF! in that case.
- other finding, major, not in findings.json: Seed workbook contains broken formulas across nine original worksheets
  - Change: graderGuidance task note item (2): names the nine #REF! links, accepts re-linking them to the agent's index prices (not an over-edit) or leaving them, and accepts the Accum Prod Mo Value column omitted or #REF! in that case.
- other finding, minor, not in findings.json: Ground-truth rep assignments contradict the Summary tab
  - Change: graderGuidance task note item (3): rep names copied from the summary tab are accepted.
