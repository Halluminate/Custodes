# Changes: FINCH task-054

Fix summary (from the fix record):

Full pass: the FINCH reference no longer shifts the source's log-return columns or retypes their header; only the requested result cells differ from the source.

Changed files (in this folder):

- reference/gt_54_ref_0.xlsx

## Fixed

- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: Same GT fix as another finding (not listed): the reference no longer carries the E:G shift or E2 header change.
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Same GT fix as another finding (not listed): the reference no longer carries the E:G shift or E2 header change.
- other finding, major, not in findings.json: The ground truth rewrites the source's existing log-return columns, against the prompt's own preserve-contents rule
  - Change: gt_54_ref_0.xlsx (XML edit): correlation!E3:G138 restored to the source's log-return cells (E3:G3 empty, E4:G138 =LN(A4/A3)... with the source's cached values), E2 header back to the source's 'LN of BSCTMP', and the volatility formulas N7:N9 now read E4:E138/F4:F138/G4:G138 (same values, 0.2007/0.1561/0.1886). calcChain E3/F3/G3 entries moved to row 138. The reference now differs from the source only in the requested result cells (I1:N9).
