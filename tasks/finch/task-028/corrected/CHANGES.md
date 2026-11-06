# Changes: FINCH task-028

Fix summary (from the fix record):

The reference counted the Canada sheet header 'CANADA' as an employee (11 instead of 10), so its total was 855. The key now says 10 and 854, and one guidance sentence lets the judge accept either reading of two debatable roster counts (Canada Support HR vacancy, Market Risk line). Full pass: the key's 'Gas Book Running' label (no source support) is back to the source's 'Gas Risk'.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_28_ref_0.xlsx

## Fixed

- [F3](../findings.json) (Verification): Answer key gives 11 for the Canada 'Canada' sub-department, but its roster block lists 10 names
  - Change: ground_truth/gt_28_ref_0.xlsx: Master!L24 (Canada / Canada) 11 -> 10 and cached Master!L73 (=SUM(L7:L71)) 855 -> 854; XML-only edit, no other cell changed.
- [F2](../findings.json) (Verification): Ground truth (gt_28_ref_0.xlsx) overcounts the 'Canada' roster sheet by including the header cell A1='CANADA' and restructures Canada sub-departments without specification, making the reference grand total wrong
  - Change: Same GT edit: Canada block now 10 (A2:A11) and total 854. The reference's split of Canada into Canada/Trading/Origination/Toronto matches the sheet's sections (Origination 11 = Power Orig 5 + Gas Orig 6) and was kept.
- [F1](../findings.json) (Verification): Reference headcount summary disagrees with the detailed rosters
  - Change: Same GT edit for Canada; graderGuidance: appended one sentence to the opening paragraph: 'Two roster counts are open to judgment, so accept either reading and the grand total that follows from it: Canada Support may be 33 or 32 (the 'Vacancy', 'HR' row 17 left out), and a 'Market Risk & Research' line of 11 may be added or left out.'
- other finding, minor, not in findings.json: Ground truth renames 'Gas Risk' on Master to 'Gas Book Running', a label that does not appear anywhere in the source workbook
  - Change: files/gt/gt_28_ref_0.xlsx (built on the critical-pass key; XML-only, one cell): Master!D43 'Gas Book Running' -> 'Gas Risk' (reuses the existing shared string), the source Master!C36 label, which matches the roster sheet 'Gas Risk' (A1 'Gas Risk', 41 people). Count L43 = 41 unchanged; no other cell changed.
- other finding, major, not in findings.json: Answer key renames 'Gas Risk' to 'Gas Book Running', which no source supports, and restructures the Canada labels
  - Change: Same key edit (Master!D43 back to 'Gas Risk'). 'Power Risk' (matches its sheet name) and the Canada split (reviewed in the critical pass) are kept.
