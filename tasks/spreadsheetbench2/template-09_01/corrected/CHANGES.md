# Changes: SpreadsheetBench 2 template-09_01

Fix summary (from the fix record):

The answer key filled Year 0 EBITDA (DebtSchedule!C8 = 55), a value no input provides and the sheet says to leave out, so no submission could pass. C8 is blank in the key again, and one prompt sentence states the key's beginning-balance interest convention.

Changed files (in this folder):

- prompt.md
- reference/gt_09_01_golden.xlsx

## Fixed

- [F4](../findings.json) (Environment & Infra): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check cannot pass (trivial fail) because DebtSchedule!C8 is None in the input workbook but 55 in the golden workbook, and because it rejects valid average-balance LBO schedules
  - Change: gt_09_01_golden.xlsx DebtSchedule!C8: 55 -> blank (now a regression cell matching the input). prompt.md: added 'Calculate each year's interest on the beginning balance of each debt tranche.' after the instruction, matching GT D9 = -0.055*180 and D10 = -0.095*55, so the average-balance reading is no longer left open.
- [F3](../findings.json) (Environment & Infra): Golden workbook contains an unprovided Year 0 EBITDA value at DebtSchedule!C8 (55 vs. None in input), making the 100%-threshold cell verifier impossible to pass
  - Change: Same GT patch (C8 blank); every other GT cell unchanged, GT scores 1.0/1.0 against itself locally.
- [F1](../findings.json) (Environment & Infra): Answer key requires a Year-0 EBITDA value (C8 = 55) that appears nowhere in the agent's materials, so the task cannot be fully passed
  - Change: Same GT patch (C8 blank).
- [F2](../findings.json) (Environment & Infra): Verifier requires a Year 0 EBITDA value absent from the supplied assumptions
  - Change: Same GT patch (C8 blank).
