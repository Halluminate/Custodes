# Changes: FINCH task-131

Fix summary (from the fix record):

Restored the unrelated G44 value the reference had deleted, and a guidance note accepts either treatment of the unlinked meter sheet.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_131_ref_0.xlsx

## Fixed

- other finding, major, not in findings.json: Companion sheet 'Mtr 98-1428' still uses the 18,000 base in the ground truth, so the GT workbook disagrees with itself on swing and buyback
  - Change: graderGuidance: task note after the opening paragraph accepts the 'Mtr 98-1428' noms either left at 18,000 (as the reference) or set to 17,000, not counted as an over-edit.
- other finding, minor, not in findings.json: Ground truth deletes an unrelated hardcoded value (G44 = 252640) that the instruction never mentions
  - Change: gt_131_ref_0.xlsx (XML-level): 'Beaumont Worksheet'!G44 restored to 252640 as in the source (same style s=2). No other cell, formula or cached value changed; it is a constant that no formula reads, so no recalc was needed.
