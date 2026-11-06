# Changes: GDPval b39a5aa7-cd1b-47ad-b249-90afd22f8f21

Fix summary (from the fix record):

Expert workbook's Year + 2 Principal Pay now reads the Year + 2 premium inputs instead of the current-year column (formula text only, values unchanged).

Changed files (in this folder):

- reference/gt_Orchestra_Compensation.xlsx

## Fixed

- other finding, major, not in findings.json: Ground-truth workbook has a broken column reference in Year + 2 Principal Pay formulas and omits input fields for several drivers required by the rubric
  - Change: gt_Orchestra_Compensation.xlsx: 'EE Calcs (Yr+2)'!F4:F106 lookup changed from MATCH("Current",Summary!$B$4:$E$4,FALSE) to MATCH("Year + 2",Summary!$B$4:$E$4,FALSE), so the Year + 2 titled-position premiums (Summary!E7:E9) drive Year + 2 Principal Pay like the Yr+1 sheet does. Formula text only, edited in the sheet XML; cached values are unchanged because E7:E9 equal C7:C9 (20%/10%/10%).
- other finding, major, not in findings.json: In the ground truth, the Year+2 premium rates ignore the Year+2 inputs and use the Current-year column
  - Change: Same edit as another finding (not listed).
