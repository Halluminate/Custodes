# Changes: SpreadsheetBench 2 template-11_02

Fix summary (from the fix record):

The DTL sign convention was ambiguous (footnote says deductions negative, seed D10 is a positive deduction, golden shows DTL balances positive). One prompt sentence now states it.

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, major, not in findings.json: Ambiguous and inconsistent sign convention for Deferred Tax Liability across Goodwill on Acquisition and Fair Value Adjustment Schedule
  - Change: prompt.md Instruction line: appended one sentence: 'Enter the deferred tax liability on FV adjustments as a negative deduction, and show the Deferred Tax Liability schedule balances as positive amounts.' Matches the golden (D13=-147, D32:H34 positive, D33:H33 change -9.38); golden and verifier unchanged.
- other finding, major, not in findings.json: Sign convention for the DTL schedule is unstated; the all-or-nothing grader accepts only the key's mixed signs
  - Change: prompt.md Instruction line: appended one sentence: 'Enter the deferred tax liability on FV adjustments as a negative deduction, and show the Deferred Tax Liability schedule balances as positive amounts.' Matches the golden (D13=-147, D32:H34 positive, D33:H33 change -9.38); golden and verifier unchanged.
- other finding, major, not in findings.json: Seed input enters a deduction as a positive number, against its own footnote
  - Change: Same prompt sentence: it states D13 is entered as a negative deduction, so D10's positive entry no longer sets the convention.
