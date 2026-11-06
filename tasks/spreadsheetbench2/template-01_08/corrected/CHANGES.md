# Changes: SpreadsheetBench 2 template-01_08

Fix summary (from the fix record):

Four prompt sentences state the conventions the all-or-nothing key requires but the template never gives: the IRR cell (J9), the signs of the coupon and amortization rows, the flat tax basis of the bond (whole $825 premium taxed at extinguishment) and what the Cash Impact row holds. Key and grading unchanged.

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, major, not in findings.json: Undisclosed cell location for Implied Discount Rate (J9 vs K9)
  - Change: Prompt: added after the Instruction sentence: "Put the implied discount rate in J9." (the key cell). Key unchanged.
- other finding, major, not in findings.json: Undisclosed sign convention for Operating Expenses (C6:F6), Coupon Payment (C8:F8), and Amortization (C7:F7)
  - Change: Prompt: added "Enter the coupon payment in row 8 as a positive amount and the premium amortization in row 7 as a negative amount (effective-interest expense less the coupon)." (the key's convention). Key unchanged.
- other finding, major, not in findings.json: The sign convention for premium amortization is not stated, and the grader compares signed values
  - Change: Prompt: added "Enter the coupon payment in row 8 as a positive amount and the premium amortization in row 7 as a negative amount (effective-interest expense less the coupon)." (the key's convention). Key unchanged.
- other finding, major, not in findings.json: Ambiguous definition and undisclosed sign convention for 'Cash Impact' row (C29:F29) in Tax Balance Sheet
  - Change: Prompt: added "In the Tax Balance Sheet, Cash Impact shows only the $15,000 principal repaid in 2023, as a negative amount." (key F29 = -15000, C29:E29 blank). Key unchanged.
- other finding, major, not in findings.json: What goes in the 'Cash Impact' row is unclear, and only the ground truth's reading passes
  - Change: Prompt: added "In the Tax Balance Sheet, Cash Impact shows only the $15,000 principal repaid in 2023, as a negative amount." (key F29 = -15000, C29:E29 blank). Key unchanged.
- other finding, major, not in findings.json: Inconsistent GAAP vs. Tax basis in Year 4 extinguishment gain/loss and cash tax calculation
  - Change: Prompt: added "For tax purposes, the bond stays at its $15,825 issue price until it is repaid, so the full $825 premium is taxed as a gain on extinguishment in 2023." (the key's tax basis). Key unchanged.
- other finding, major, not in findings.json: The tax treatment of the bond premium is never stated, but the all-or-nothing grade depends on it
  - Change: Prompt: added "For tax purposes, the bond stays at its $15,825 issue price until it is repaid, so the full $825 premium is taxed as a gain on extinguishment in 2023." (the key's tax basis). Key unchanged.
