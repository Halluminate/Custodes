# Changes: SpreadsheetBench 2 template-07_01

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_07_01_golden.xlsx

## Fixed

- other finding, minor, not in findings.json: Ground truth contains arithmetic errors in Shareholders' Equity and Total Liabilities & Equity (E30, E31, G60, G61)
  - Change: gt_07_01_golden.xlsx (XML edit, nothing else touched): EquityDRD!E30 2537.27 -> 2547.27 (= C30+D30, equals E60) and G60 3200.67 -> 3210.67 (= E60+F60); cached E31 4292.4 -> 4302.4 and G61 4950.67 -> 4960.67, now equal to total assets E26/G56. SB2 scorer: new key 1.0 vs itself; old key still passes (inside 1%); untouched input fails.
- other finding, minor, not in findings.json: Ground-truth balance sheet does not balance: a hardcoded equity figure is $10 short, and the error carries into 2019
  - Change: gt_07_01_golden.xlsx (XML edit, nothing else touched): EquityDRD!E30 2537.27 -> 2547.27 (= C30+D30, equals E60) and G60 3200.67 -> 3210.67 (= E60+F60); cached E31 4292.4 -> 4302.4 and G61 4950.67 -> 4960.67, now equal to total assets E26/G56. SB2 scorer: new key 1.0 vs itself; old key still passes (inside 1%); untouched input fails.
- other finding, minor, not in findings.json: Golden workbook contains two unbalanced balance sheets
  - Change: gt_07_01_golden.xlsx (XML edit, nothing else touched): EquityDRD!E30 2537.27 -> 2547.27 (= C30+D30, equals E60) and G60 3200.67 -> 3210.67 (= E60+F60); cached E31 4292.4 -> 4302.4 and G61 4950.67 -> 4960.67, now equal to total assets E26/G56. SB2 scorer: new key 1.0 vs itself; old key still passes (inside 1%); untouched input fails.
- other finding, major, not in findings.json: Sign convention for the 2019 'Deferred tax benefit (reversal)' line is unstated, and the all-or-nothing grader accepts only a negative entry
  - Change: answer_position 'EquityDRD'!B2:G61 -> 'EquityDRD'!B2:G47,'EquityDRD'!B48,'EquityDRD'!D48:G48,'EquityDRD'!B49:G61 (drops only C48, the sign-ambiguous deferred tax benefit line); C46 total taxes, C49 net income and F59 DTL reversal (-5.13) still grade the reversal. graderGuidance range text updated. Scorer: key 1.0; key with C48 = +5.13 now 1.0 (was mod 0.9825); untouched input fails.
