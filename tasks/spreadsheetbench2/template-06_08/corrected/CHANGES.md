# Changes: SpreadsheetBench 2 template-06_08

Fix summary (from the fix record):

WorkingCapital_Forecast!B17, the row the answer key fills with the Accounts Payable balance, carried a leftover footnote label instead of 'Accounts Payable'; the label is corrected in the input, the answer key and the verifier's reference copy (one cell each). The sandbox's missing openpyxl/pandas is an environment issue.

Changed files (in this folder):

- reference/gt_06_08_golden.xlsx
- reference/untouched_input_06_08_input.xlsx
- inputs/06_08_input.xlsx

## Fixed

- other finding, minor, not in findings.json: Leftover authoring label: the same footnote text appears twice, and the footnote itself has no content
  - Change: WorkingCapital_Forecast!B17 label 'FN: Cash flow sign convention for WC changes' -> 'Accounts Payable' in files/data/06_08_input.xlsx and files/gt/gt_06_08_golden.xlsx (the key's AP balance row; same cell in both so it stays a regression cell). XML edit of that one cell only. Local scorer: key vs itself 1.0/1.0, patched input fails (mod 0.0). Same one-cell edit in the verifier's reference copy files/gt/untouched_input_06_08_input.xlsx so B17 stays a regression cell.
