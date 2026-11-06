# Changes: FINCH task-033

Fix summary (from the fix record):

Grader note accepts department order or Total-sorted rows for the 'All Originators by Value' sheet, and the key no longer hides the input's visible '2Q' sheet.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_33_ref_0.xlsx

## Fixed

- other finding, major, not in findings.json: The sheet name 'by Value' suggests sorting by value, but the answer key is in department order
  - Change: graderGuidance: task-specific note added before the 'insufficient information' paragraph: "Task-specific note: the reference lists the originators in department-tab order (Asset Marketing through West Gas), one row per originator per team. 'by Value' is the sheet name, so the same rows in department order or sorted by Total are equally correct, and row order alone is not an error."
- other finding, minor, not in findings.json: The answer key hides the visible '2Q' sheet, an edit the instruction never asks for
  - Change: files/gt/gt_33_ref_0.xlsx: xl/workbook.xml only, sheet '2Q' state="hidden" removed so 2Q is visible as in the input; every other zip member byte-identical.
- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: Both changes above (row-order note, 2Q visible again in the key), which remove the verified reasons a judge can fail the key against its own instruction. Not re-run through the guidance test locally.
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Same as exploit-probe-0.
