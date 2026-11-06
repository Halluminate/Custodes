# Changes: FINCH task-039

Fix summary (from the fix record):

Full pass: grader-guidance task note accepting a Chart 2 without the TOTAL/OTHER bars the reference plots and not requiring the reference's uneven chart sizes.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Ground-truth Chart 2 plots 'OTHER' and 'TOTAL' as groups on the X-axis
  - Change: graderGuidance: added one task note: Chart 2 may leave out the TOTAL (and empty OTHER) rows that the reference plots as bars, and the reference's uneven chart sizes are not required (four similar-sized, non-overlapping charts in rows 30-80).
- other finding, minor, not in findings.json: Reference layout breaks the prompt's 'size them evenly' instruction
  - Change: graderGuidance: added one task note: Chart 2 may leave out the TOTAL (and empty OTHER) rows that the reference plots as bars, and the reference's uneven chart sizes are not required (four similar-sized, non-overlapping charts in rows 30-80).
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: graderGuidance: added one task note: Chart 2 may leave out the TOTAL (and empty OTHER) rows that the reference plots as bars, and the reference's uneven chart sizes are not required (four similar-sized, non-overlapping charts in rows 30-80).
