# Changes: FINCH task-129

Fix summary (from the fix record):

The reference chart title now uses the capitalisation the prompt asks for.

Changed files (in this folder):

- reference/gt_129_ref_0.xlsx

## Fixed

- other finding, minor, not in findings.json: Chart title capitalization in the answer key does not match the title the prompt asks for
  - Change: gt_129_ref_0.xlsx, xl/charts/chart1.xml title run: 'Rolling 55 day payables (as of the 25th of the month)' -> 'Rolling 55 Day Payables (as of the 25th of the Month)' (exact prompt text). XML-level, nothing else changed.
