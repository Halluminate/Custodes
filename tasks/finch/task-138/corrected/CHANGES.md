# Changes: FINCH task-138

Fix summary (from the fix record):

The answer key's footnotes carry author-computed point figures that no source tab has; the guidance now accepts source-style footnotes. Two unlabeled scratch values in the key's hidden row 12 are removed.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_138_ref_0.xlsx

## Fixed

- other finding, major, not in findings.json: Prompt leaves the page contents unstated, but the pass/fail grader requires a match to one specific reference layout
  - Change: graderGuidance: one sentence added after the opening paragraph: 'Footnotes may follow the wording of the source summary tabs; the reference's reworded footnotes and their point figures are not required.'
- other finding, minor, not in findings.json: Reference sheet has a hidden row holding two unlabeled 0.335 values
  - Change: gt_138_ref_0.xlsx 'P&C': the two unlabeled scratch values F12 and L12 (0.335, hidden row 12) removed (XML edit, cells keep their style). No other cell changed.
