# Changes: FINCH task-021

Fix summary (from the fix record):

Prompt now says to add the 12/31/2001 column after 12/28/2001 (the source has no such column to update).

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, minor, not in findings.json: The prompt says to 'update' a 12/31/2001 column that is not in the source workbook, and says nothing about the Total column
  - Change: Prompt: 'update the 12/31/2001 (Mon) column' became 'add a 12/31/2001 (Mon) column after the 12/28/2001 column', since the source stops at 12/28/2001 (AQ) and the answer key inserts the new column at AS, before Total. Nothing else changed.
