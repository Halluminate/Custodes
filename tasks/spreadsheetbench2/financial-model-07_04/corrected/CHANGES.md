# Changes: SpreadsheetBench 2 financial-model-07_04

Fix summary (from the fix record):

Recalculated the stale golden and reference workbooks so the answer key passes its own check, and rewrote the two prompt sentences (Equity Distribution, Equity Balance) to describe the graded formulas.

Changed files (in this folder):

- prompt.md
- reference/gt_07_RealEstate_golden.xlsx
- reference/untouched_input_07_04_RealEstate_input.xlsx

## Fixed

- [F10](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells trivially fails (scores 0.0 across all units) because it recalculates only the agent's output workbook in LibreOffice 26.2 while comparing against un-recalculated LibreOffice 7.3 ground truth and reference workbooks
  - Change: Replaced the answer key and the reference workbook with copies force-recalculated through the verifier's own LibreOffice path, so their cached values are live (formulas unchanged); the recalculated golden now scores 1.0 against itself (regression 1.0, modification 1.0).
- [F9](../findings.json) (Verification): Golden gate: the ground-truth deliverable does not score full reward
  - Change: Replaced the answer key and the reference workbook with copies force-recalculated through the verifier's own LibreOffice path, so their cached values are live (formulas unchanged); the recalculated golden now scores 1.0 against itself (regression 1.0, modification 1.0).
- [F4](../findings.json) (Verification): Ground truth and reference workbooks contain stale cached values from LibreOffice 7.3 where XLOOKUP evaluated to #NAME?, causing the golden workbook to fail its own verifier after LibreOffice 26.2 recalculation
  - Change: Replaced the answer key and the reference workbook with copies force-recalculated through the verifier's own LibreOffice path, so their cached values are live (formulas unchanged); the recalculated golden now scores 1.0 against itself (regression 1.0, modification 1.0).
- [F3](../findings.json) (Verification): Answer-key workbook has wrong cached values (sales revenue is 0) and scores 0 against its own verifier
  - Change: Replaced the answer key and the reference workbook with copies force-recalculated through the verifier's own LibreOffice path, so their cached values are live (formulas unchanged); the recalculated golden now scores 1.0 against itself (regression 1.0, modification 1.0).
- [F2](../findings.json) (Verification): The golden workbook fails its own verifier after mandatory recalculation
  - Change: Replaced the answer key and the reference workbook with copies force-recalculated through the verifier's own LibreOffice path, so their cached values are live (formulas unchanged); the recalculated golden now scores 1.0 against itself (regression 1.0, modification 1.0).
- [F6](../findings.json) (Verification): Requirement for 'Equity Distribution During Project' contradicts the ground truth formula in Cashflow (Monthly)!J87:CP87
  - Change: prompt.md: replaced the Equity Distribution sentence with "Calculate Equity Distribution During Project for Years 1–7 as positive Net Project Cashflows multiplied by the dividend payout ratio, using the Period 1 ratio for months up to and including the Period 2 start date from Inputs and the Period 2 ratio after it." (matches GT J87, which is ratio x MAX(J84,0); the SUM(J74:$BG$74)=0 branch is inert because J84 is 0 wherever it fires, checked on every column J:CP)
- [F5](../findings.json) (Verification): Equity Distribution GT formula does not follow its description, and its reference pattern breaks halfway across the row
  - Change: prompt.md: replaced the Equity Distribution sentence with "Calculate Equity Distribution During Project for Years 1–7 as positive Net Project Cashflows multiplied by the dividend payout ratio, using the Period 1 ratio for months up to and including the Period 2 start date from Inputs and the Period 2 ratio after it." (matches GT J87, which is ratio x MAX(J84,0); the SUM(J74:$BG$74)=0 branch is inert because J84 is 0 wherever it fires, checked on every column J:CP)
- [F1](../findings.json) (Task Spec): Requirement for 'Equity Balance' states 'maximum of Opening Balance, Equity Injection, Equity Distribution During Project, Equity Balloon Payment, and Total Equity Payout' instead of the net sum floored at zero used in ground truth
  - Change: prompt.md: replaced the Equity Balance sentence with "Calculate Equity Balance for Years 1–7 as Net Project Cashflows plus Opening Balance plus Equity Injection less Total Equity Payout, floored at zero for each period." (matches GT J90 =ROUND(MAX(J84-J89+J85+J86,0),5), checked on every column)
- [F7](../findings.json) (Task Spec): Equity Balance instruction does not describe the GT formula
  - Change: prompt.md: replaced the Equity Balance sentence with "Calculate Equity Balance for Years 1–7 as Net Project Cashflows plus Opening Balance plus Equity Injection less Total Equity Payout, floored at zero for each period." (matches GT J90 =ROUND(MAX(J84-J89+J85+J86,0),5), checked on every column)
- [F8](../findings.json) (Verification): The stated Equity Balance calculation contradicts the answer key
  - Change: prompt.md: replaced the Equity Balance sentence with "Calculate Equity Balance for Years 1–7 as Net Project Cashflows plus Opening Balance plus Equity Injection less Total Equity Payout, floored at zero for each period." (matches GT J90 =ROUND(MAX(J84-J89+J85+J86,0),5), checked on every column)
