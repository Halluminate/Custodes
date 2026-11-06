# Changes: SpreadsheetBench 2 debugging-03_03

Fix summary (from the fix record):

Added one prompt sentence giving the labels and row positions of the deleted rows, which the golden requires exactly and the input never reveals.

Changed files (in this folder):

- prompt.md

## Fixed

- [F3](../findings.json) (Verification): Rebuilt rows must contain exact label text the agent has no way to know, and the check is pass/fail on every changed cell
  - Change: Prompt: added one sentence after the reference data naming the deleted rows, where they go and their labels, all as in the golden: LBO rows 4-5 'Master Control' and 'Units Converter' (1,000,000), LBO row 13 'Transaction Fees' below 'Exit EBITDA Multiple', and 'Ex 12 - Debt Schedule' row 9 'Revolver (max $150 million)'. The positional, exact-string check now has a knowable target. The golden still grades 1.0 locally.
- [F1](../findings.json) (Task Spec): Grading depends on putting deleted rows back at exact row numbers that nothing in the input reveals
  - Change: Prompt: added one sentence after the reference data naming the deleted rows, where they go and their labels, all as in the golden: LBO rows 4-5 'Master Control' and 'Units Converter' (1,000,000), LBO row 13 'Transaction Fees' below 'Exit EBITDA Multiple', and 'Ex 12 - Debt Schedule' row 9 'Revolver (max $150 million)'. The positional, exact-string check now has a knowable target. The golden still grades 1.0 locally.
- [F2](../findings.json) (Task Spec): Grading requires undisclosed wording and placement for deleted controls
  - Change: Prompt: added one sentence after the reference data naming the deleted rows, where they go and their labels, all as in the golden: LBO rows 4-5 'Master Control' and 'Units Converter' (1,000,000), LBO row 13 'Transaction Fees' below 'Exit EBITDA Multiple', and 'Ex 12 - Debt Schedule' row 9 'Revolver (max $150 million)'. The positional, exact-string check now has a knowable target. The golden still grades 1.0 locally.
