# Changes: FINCH task-086

Fix summary (from the fix record):

Prompt now says the percentages are rounded to two decimal places of a percent. A grader note accepts either the reference's relabelled rows 41-43 or the template's own fields (B40, B43:B45, B46 sum check), and lets the sum confirmation be a cell or a line in answer.txt.

Changed files (in this folder):

- prompt.md
- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Ground-truth workbook gt_86_ref_0.xlsx does not match the source template 86_src_0.xlsx and omits Row 46 (the 100% sum confirmation row)
  - Change: graderGuidance: task-specific note added before the 'insufficient information' paragraph: "Task-specific note: the reference writes Total Investments in B40 and the three percentages in B41:B43 with relabelled rows, unrounded but shown with two decimals (6.26%, 47.25%, 46.48%), and it does not keep the template's rows 43-46. Filling the template's own fields instead (Total in B40, Cash %, Equity % and Fixed Income % in B43:B45, a sum check such as B46) is equally correct, values rounded to two decimal places of a percent match the reference, and the sum confirmation may be a cell or a line in answer.txt."
- other finding, major, not in findings.json: The GT changes the source template's layout: it drops the labelled percentage rows and the 100% check row the prompt asks the agent to fill
  - Change: Same graderGuidance note as another finding (not listed) (template positions B40, B43:B45 and a B46 sum check accepted).
- other finding, major, not in findings.json: The prompt asks for a sum confirmation the answer key never makes; the source's check cell is a hardcoded 1
  - Change: Same graderGuidance note as another finding (not listed) (the sum confirmation may be a cell such as B46 or a line in answer.txt, and is not required to have a counterpart in the reference).
- other finding, major, not in findings.json: Prompt instruction to "round each to two decimals" and "confirm the three sum to approximately 100%" conflicts with unrounded values in gt_86_ref_0.xlsx
  - Change: problemStatement, one phrase in one sentence: 'round each to two decimals,' -> 'round each to two decimal places as a percentage (for example 12.34%),'; the same graderGuidance note as another finding (not listed) accepts the reference's unrounded values shown as 0.00% or values rounded to two decimal places of a percent.
- other finding, major, not in findings.json: The prompt's 'round each to two decimals' contradicts the answer key, which does no rounding
  - Change: Same prompt phrase change and guidance note as another finding (not listed).
