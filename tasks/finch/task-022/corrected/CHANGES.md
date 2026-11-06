# Changes: FINCH task-022

Fix summary (from the fix record):

Not changed. Both findings are about the LibreOffice-backed MCP excel tools (pivot labels re-rendered as '... Result', a phantom DPCache sheet), not about the task files. Full pass: grader guidance gained a task-specific note (expected change, out-of-scope blocks, refreshed or hand-corrected pivot both OK, LibreOffice Result labels).

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: graderGuidance: added a task-specific note after the opening paragraph stating the reference change (E15:E17 -32,000 -> -16,000, E30 295,645, AD30 3,340,795, rows 79-92 follow), that other blocks are unchanged by design, and that LibreOffice "... Result" labels are not a difference. Official judge text kept verbatim.
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Same graderGuidance note as exploit-probe-0.
- other finding, major, not in findings.json: The source pivot is bound to an external Enron file, and it is unclear whether hand-editing the displayed pivot cells counts as 'updating the pivot'
  - Change: Same graderGuidance note: either a refreshed pivot or directly corrected pivot cells is accepted, as long as the table stays a pivot table and shows the corrected values.
