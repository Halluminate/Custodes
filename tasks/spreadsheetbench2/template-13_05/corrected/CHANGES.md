# Changes: SpreadsheetBench 2 template-13_05

Fix summary (from the fix record):

The Q3 note said reported opex 'excludes' the $18 gain while the answer key adds $18 back. I changed the note to 'includes' in the input, reference and golden workbooks so the note matches the graded adjustment. Full pass: two prompt sentences state the key's untaxed normalization and once-per-column growth, and the undefined Q1 2024 growth cell C21 is dropped from the compared range so N/A is not penalised.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_13_05_golden.xlsx
- reference/untouched_input_13_05_input.xlsx
- inputs/13_05_input.xlsx

## Fixed

- [F1](../findings.json) (Verification): Q3 nonrecurring note says opex 'excludes' the gain, yet the ground truth adds $18 back (contradictory requirement)
  - Change: Normalize!B29 note changed from 'Q3 2024: Operating Expenses excludes $18 insurance settlement gain' to '... includes $18 insurance settlement gain' (same wording as the sibling 13_04 task), so the answer key's add-back E10 = E34+18 follows from the note. Edited the shared string only, identically in the input (13_05_input.xlsx), the verifier reference (untouched_input_13_05_input.xlsx) and the golden (gt_13_05_golden.xlsx), so B29 stays an unchanged regression cell.
- other finding, major, not in findings.json: Ground truth labels reported tax as 'Normalized Tax Expense' and does not tax-effect the adjustments
  - Change: problemStatement: added one sentence to the Instruction: "Use each quarter's reported tax expense as its normalized tax expense, without tax-effecting the adjustments." (the key's C14:E14 = C35:E35).
- other finding, major, not in findings.json: Forecast calendar skips a quarter without a matching growth bridge
  - Change: problemStatement: added one sentence to the Instruction: "Apply the forecast growth rate once per projected column." (the key's F7 =E7*(1+F21), G7 =F7*(1+G21)).
- other finding, major, not in findings.json: Vague instruction defers all methodology to in-sheet notes; key modeling choices are unstated
  - Change: Same two prompt sentences as another finding (not listed) (tax) and another finding (not listed) (growth per projected column).
- other finding, major, not in findings.json: Undefined Q1 2024 growth rate: entering 'N/A' fails the whole task because the ground truth expects 0
  - Change: verifications[0].parameters.answer_position 'Normalize'!B2:I35 -> 'Normalize'!B2:I20,'Normalize'!B21,'Normalize'!D21:I21,'Normalize'!B22:I35 (Normalize!C21, the undefined Q1 2024 growth, is no longer compared); graderGuidance range text updated to match. Local SB2 scorer: golden 1.0, golden with C21 = 'N/A' 1.0 (was 0 under the old range), untouched input fails.

## Confirmed findings not fixed

- [F2](../findings.json): Q3 normalization note contradicts the graded adjustment
  - Reason: duplicate-of:F1
