# Changes: SpreadsheetBench 2 financial-model-18_01

Fix summary (from the fix record):

Aligned the golden workbook with the prompt: PAT Margin now shows NM only when Total Income is zero or negative, and the unrequested 'Esc. %' label in P&L!A13 is removed. The patched golden scores 1.0 locally. The prompt now states the balance-check form (total liabilities and equity minus total assets), which the seed residual makes score-sensitive.

Changed files (in this folder):

- prompt.md
- reference/gt_18_RoadAssets_golden.xlsx

## Fixed

- [F3](../findings.json) (Verification): P&L PAT Margin 'NM' condition in prompt contradicts golden workbook formula and values at P&L!J35 and P&L!Q35
  - Change: Golden gt_18_RoadAssets_golden.xlsx: P&L!C35:Q35 changed from =IF(X34/X12<0,"NM",X34/X12) to =IF(X12<=0,"NM",X34/X12) as the prompt states, then recalculated in LibreOffice; J35 and Q35 now hold -0.0090 and -0.0247 instead of 'NM'. No other value changed.
- [F4](../findings.json) (Verification): Ground-truth PAT Margin applies the wrong 'NM' rule: it shows NM when PAT is negative, not when Total Income is zero or negative
  - Change: Golden gt_18_RoadAssets_golden.xlsx: P&L!C35:Q35 changed from =IF(X34/X12<0,"NM",X34/X12) to =IF(X12<=0,"NM",X34/X12) as the prompt states, then recalculated in LibreOffice; J35 and Q35 now hold -0.0090 and -0.0247 instead of 'NM'. No other value changed.
- [F1](../findings.json) (Verification): PAT Margin answer key contradicts the explicit NM condition
  - Change: Golden gt_18_RoadAssets_golden.xlsx: P&L!C35:Q35 changed from =IF(X34/X12<0,"NM",X34/X12) to =IF(X12<=0,"NM",X34/X12) as the prompt states, then recalculated in LibreOffice; J35 and Q35 now hold -0.0090 and -0.0247 instead of 'NM'. No other value changed.
- [F5](../findings.json) (Task Spec): Undisclosed modification at P&L!A13 ('Esc. %') required by golden workbook but omitted from instructions
  - Change: Golden gt_18_RoadAssets_golden.xlsx: cleared the unrequested 'Esc. %' label in P&L!A13 so it matches the input and becomes a regression cell. No other value changed.
- [F6](../findings.json) (Verification): Ground truth adds an unrequested 'Esc. %' label in P&L!A13, and the all-or-nothing grader requires it
  - Change: Golden gt_18_RoadAssets_golden.xlsx: cleared the unrequested 'Esc. %' label in P&L!A13 so it matches the input and becomes a regression cell. No other value changed.
- [F2](../findings.json) (Verification): An undisclosed text insertion is mandatory for passing
  - Change: Golden gt_18_RoadAssets_golden.xlsx: cleared the unrequested 'Esc. %' label in P&L!A13 so it matches the input and becomes a regression cell. No other value changed.
- other finding, major, not in findings.json: Undisclosed sign convention for Balance Sheet integrity check (BS!C26:T26) causesTotal Assets minus Total Liabilities to fail
  - Change: prompt.md: the BS check clause now reads 'add a balance sheet integrity check for FY22–FY39 calculated as total liabilities and equity minus total assets', the golden's =C15-C23 form. GT and grading unchanged.
- other finding, major, not in findings.json: Balance sheet check rejects valid alternatives: GT requires Liabilities minus Assets, so a natural Assets minus Liabilities or TRUE/FALSE check fails
  - Change: Same prompt clause (check form and sign stated).
- other finding, major, not in findings.json: Balance-sheet checks expose unexplained residuals and an unstated sign convention
  - Change: Same prompt clause (check form and sign stated).
