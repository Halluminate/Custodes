# Changes: FINCH task-032

Fix summary (from the fix record):

The answer key gave Fundamentals-Power a supervisor the source never lists. It now leaves that cell blank, as it already does for ERCOT-Power. Full pass: the reference no longer edits two 'Rotation list' cells, and the grader accepts East Gas Trading under either business line, since the source sheets disagree.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_32_ref_0.xlsx

## Fixed

- [F2](../findings.json) (Verification): Ground truth workbook has wrong line supervisor ('Will Lloyd / Davis Dana') and unresolvable supervisor for Fundamentals-Power
  - Change: files/gt/gt_32_ref_0.xlsx: Requirements!B13 (Fundamentals-Power line supervisor) cleared; it held 'Will Lloyd / Davis Dana', which belongs to N/E Fundamentals. The source leaves 'Rotation list'!E5 blank, so the key now leaves it blank the same way it already does for ERCOT-Power (B23). No other cell changed.
- [F1](../findings.json) (Verification): The answer key gives Fundamentals-Power a supervisor that the source workbook never lists
  - Change: Same GT change as F2 (Requirements!B13 cleared).
- [F3](../findings.json) (Environment & Infra): Required Fundamentals-Power supervisor is missing
  - Change: Same GT change as F2 (Requirements!B13 cleared).
- other finding, major, not in findings.json: Source workbook conflict on 'East Gas Trading' business line (Gas vs Power) and 'Noms' multi-supervisor / 'Norms' typo causes ground-truth mismatch
  - Change: graderGuidance task note: East Gas Trading accepted under Gas (Rotation list) or Power (Rotation chart and reference) with supervisor Neal Scott and 0/1 counts. The Noms part needs no change: as of March 1 only Bob Superty supervises Noms (McMichael and 'Norms' are August rotations).
- other finding, major, not in findings.json: East Gas Trading is assigned to conflicting business lines
  - Change: Same East Gas Trading task note as another finding (not listed).
- other finding, major, not in findings.json: Ground truth modifies original sheet 'Rotation list' while prompt and rubric forbid modifying original sheets
  - Change: files/gt/gt_32_ref_0.xlsx: 'Rotation list'!E4 back to 'Kayne Coulter' and D12 back to 'Real Time' (source values), by repointing the two cells' shared-string indices in sheet1.xml; no other part of the file touched (built on the critical-pass GT). Task note adds that output must keep original sheets unchanged.
- other finding, major, not in findings.json: The answer key changes original source cells that the task never asks to change
  - Change: Same GT revert of Rotation list E4/D12 as another finding (not listed).
