# Changes: FINCH task-076

Fix summary (from the fix record):

Full pass: grader note so the undefined 'titles' is not graded against the reference's exact choice of bold cells.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: "Titles" is undefined, and the binary grader compares against a GT that bolds the sheet title, a stray header fragment and the header row
  - Change: grader_guidance.md: one task note after the opening paragraph: 'titles' is undefined, so an output that bolds the row-4 column headings with or without the F1 sheet title and the I3 'Level of' line is not failed on that basis. Reference unchanged.
