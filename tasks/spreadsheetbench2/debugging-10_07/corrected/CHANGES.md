# Changes: SpreadsheetBench 2 debugging-10_07

Fix summary (from the fix record):

No change. The golden workbook's circular-block caches fail the forced LibreOffice recalculation, and because that recalculation does not converge, no recomputed answer key passes every correct output. Full pass: answer_position now leaves out five float-residue check cells, the six lookup label cells, the mislabeled P&L row 27 and two non-tying FY2024A balance-sheet subtotals; the key's P&L B28 typo 'Payrol' is corrected. Cleanup pass: the cells on which the golden failed its own check (circular-block dependents and line-break label formulas) are now left out of answer_position, so the golden scores 1.0.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_10_golden.xlsx

## Fixed

- other finding, major, not in findings.json: Floating-point noise cells are graded as required modifications
  - Change: answer_position: '4-Wall Analysis'!A2:DX1443 split to leave out the five zero-check cells whose input and key values are both float residues below 1e-15 and nonzero (AR867, AR939, AR1011, BE1083, BE1155), which the relative tolerance can never match after a recalc. Verifier id, name, function, weight and mode unchanged; grader guidance range text updated. Golden still fails its own check because of the unconverged circular block (verifier-correctness-0, not fixed); none of the remaining golden errors involve the cells changed here.
- other finding, major, not in findings.json: Open-ended audit prompt is graded as all-or-nothing against one specific set of fixes, including label text
  - Change: answer_position: 'P&L Summary'!B48:B50 and E48:E50 (the lookup labels the key rewrites to '(-) OpEx' etc.) left out, so a fix that repairs the F48:F50 lookups another way is not failed on label text; F46:F51 still graded. Golden still fails its own check because of the unconverged circular block (verifier-correctness-0, not fixed); none of the remaining golden errors involve the cells changed here.
- other finding, minor, not in findings.json: Mislabeled and misspelled rows are left in the model even though the task asks the agent to fix naming issues
  - Change: gt_10_golden.xlsx 'P&L Summary'!B28 corrected to "(+) Add'l Corp. / Payroll Syn." (new shared string; Model!B102, which shared the old string, left unchanged). 'P&L Summary'!B27 ('Memo: Rent % of Administrative' over Credit Card Charges / Administrative) has no single defensible wording, so it is left out of answer_position. Untouched input now also fails on B28. Golden still fails its own check because of the unconverged circular block (verifier-correctness-0, not fixed); none of the remaining golden errors involve the cells changed here.
- other finding, minor, not in findings.json: Historical balance-sheet source figures do not reconcile
  - Change: answer_position: 'FY2024A (BS)'!C48 and F57 left out. These hardcoded subtotals do not tie to their components (C48 omits income taxes payable of 9,815,955, F57 is 32,884,297 above F51:F56) and there is no source to say whether the subtotal or the components are wrong. Golden still fails its own check because of the unconverged circular block (verifier-correctness-0, not fixed); none of the remaining golden errors involve the cells changed here.
- [F5](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells is a trivial fail (0.0 on all units and 0.0 on the golden workbook itself) due to multi-pass circular-reference drift between gt_10_golden.xlsx and single-pass LibreOffice recalculation
  - Change: Cleanup pass (rule 5): the cells on which the golden fails its own check are left out of answer_position (166 Model and 16 P&L Summary cells downstream of the unconverged circular block, 84 '4-Wall Analysis' label-formula cells whose cached line break does not survive the recalc). Real SB2 scorer: golden 1.0, openpyxl-saved golden 1.0, untouched input FAIL (mod 0.0).

## Confirmed findings not fixed

- [F4](../findings.json): Golden gate: the ground-truth deliverable does not score full reward
  - Reason: duplicate-of:verifier-correctness-0
- [F3](../findings.json): Golden workbook (gt_10_golden.xlsx) contains unconverged circular-reference cached values in Model that fail the verifier's own single-pass LibreOffice recalculation
  - Reason: duplicate-of:verifier-correctness-0
- [F2](../findings.json): The ground-truth workbook fails its own verifier, so the task can't be passed
  - Reason: duplicate-of:verifier-correctness-0
- [F1](../findings.json): Golden workbook fails its own forced-recalculation grading
  - Reason: duplicate-of:verifier-correctness-0
