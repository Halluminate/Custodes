# Changes: FINCH task-105

Fix summary (from the fix record):

Prompt names the HPL 'Huntv,Woodls,Conroe' line as the one that becomes 6,000.

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, minor, not in findings.json: Ambiguous 'Houston Pipe Line should be 6,000 (instead of 9,000)': no 'Houston Pipe Line' line holds 9,000 on 2/10
  - Change: Prompt: 'Houston Pipe Line should be 6,000 (instead of 9,000)' became "the Houston Pipe Line 'Huntv,Woodls,Conroe' line should be 6,000 (instead of 9,000)", naming the row the reference changes (row 14, =SUM(N59:N61) = 1,000 + 5,000 + 0). Before, it could be read as HPL Points (row 10, 200,000), which the reference keeps.
- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: Same prompt change. The guidance test scored the GT 0.00, 0.00, 0.92. The likely cause is the old wording, which a grader can read as requiring HPL Points (N10) = 6,000, so the reference's N10 = 200,000 looked wrong. Rerun the probe to confirm.
