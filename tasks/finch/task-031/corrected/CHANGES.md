# Changes: FINCH task-031

Fix summary (from the fix record):

The reference Rotation chart gave the Gas-section employee Vladi Pimenov a '-Power' suffix, left an unlabeled yellow August gap for Russell Ballato and Juan Padron, and ran rotation fills past December into unheaded columns P:Q. The reference now labels him '-Gas', starts their Book Running block in August, and stops all fills at December. Full pass: the key's Rotation list is back to the source (the task says to preserve original sheets), and a guidance note accepts 'Norms' or 'Noms' for Matt Smith's August rotation.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_31_ref_0.xlsx

## Fixed

- [F1](../findings.json) (Verification): Ground truth Rotation chart contains corrupted rotation timelines, unlabeled gap cells, out-of-2001 spillover columns, and a wrong group suffix (-Power instead of -Gas)
  - Change: gt_31_ref_0.xlsx 'Rotation chart' (workbook has no formulas, edited with openpyxl): E21 'East Gas Trading-Power' -> 'East Gas Trading-Gas'; merge E21:P21 -> E21:O21; K7 and K13 yellow gap fill replaced by the Book Running block fill so that rotation starts 2001-08 as in Rotation list; fills removed from P:Q in every row (no month header there, all cells empty). No cell value other than E21 changed.
- [F3](../findings.json) (Verification): Answer key gives Vladi Pimenov, a Gas-section employee, the suffix '-Power'
  - Change: Same GT edit: 'Rotation chart'!E21 now 'East Gas Trading-Gas'.
- [F2](../findings.json) (Verification): Reference assigns a gas employee the power suffix
  - Change: Same GT edit: 'Rotation chart'!E21 now 'East Gas Trading-Gas'.
- other finding, major, not in findings.json: Ground truth modifies the original 'Rotation list' sheet despite prompt requiring preservation of all original sheets and their contents
  - Change: files/gt/gt_31_ref_0.xlsx (built on the critical-pass key, already an openpyxl save): 'Rotation list'!G5:H20 restored to the source values (27 cells: blanks back in G5:H5 and G12:H12, the original order, no added 'Schwieger Jim'/'Shively Hunter'/'Sturm Fletcher' in column G). Rotation list now equals the source exactly; no style and no other sheet changed.
- other finding, major, not in findings.json: Answer key changes an original sheet the task says to preserve (Rotation list, columns G/H)
  - Change: Same GT edit: 'Rotation list' G5:H20 restored to the source.
- other finding, minor, not in findings.json: Source data has an unmarked 'Norms' typo for 'Noms', which the GT silently corrects
  - Change: grader guidance: added 'Task note for this problem: Rotation list D39 spells Matt Smith's August 2001 group 'Norms', a typo for the Noms group named in the other entries, so accept either spelling with the gas suffix for that rotation.'
