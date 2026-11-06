# Changes: SpreadsheetBench 2 template-01_05

Fix summary (from the fix record):

The prompt now states the balance-sheet column layout and tax basis the answer key uses; the answer key's deferred-tax design was left as is.

Changed files (in this folder):

- prompt.md

## Fixed

- [F1](../findings.json) (Task Spec): Ambiguous Balance Sheet column timeline (`BOP 2018` vs year-end columns) and undisclosed tax basis conventions
  - Change: prompt.md: added "On the GAAP and Tax balance sheets, enter each year's activity starting in the BOP 2018 column (2018 under BOP 2018 through 2021 under 12/31/2020), show only the principal repayment at maturity in the 12/31/2021 column, and use the $12,000 face value as the bond's tax basis." which states the column layout and tax basis the answer key uses (GT C33:C35 2018 activity under BOP 2018, F35 12000, G-column repayment, C47 12000).
- [F4](../findings.json) (Verification): Ground-truth balance-sheet values sit one column off from their period headers
  - Change: prompt.md: added "On the GAAP and Tax balance sheets, enter each year's activity starting in the BOP 2018 column (2018 under BOP 2018 through 2021 under 12/31/2020), show only the principal repayment at maturity in the 12/31/2021 column, and use the $12,000 face value as the bond's tax basis." which states the column layout and tax basis the answer key uses (GT C33:C35 2018 activity under BOP 2018, F35 12000, G-column repayment, C47 12000).
- [F3](../findings.json) (Verification): Answer key shifts balance-sheet activity one period earlier than the supplied headers
  - Change: prompt.md: added "On the GAAP and Tax balance sheets, enter each year's activity starting in the BOP 2018 column (2018 under BOP 2018 through 2021 under 12/31/2020), show only the principal repayment at maturity in the 12/31/2021 column, and use the $12,000 face value as the bond's tax basis." which states the column layout and tax basis the answer key uses (GT C33:C35 2018 activity under BOP 2018, F35 12000, G-column repayment, C47 12000).

## Confirmed findings not fixed

- [F2](../findings.json): GT keeps a $144 deferred tax liability after the bond is retired and classifies the temporary difference with the wrong sign
  - Reason: cannot-fix-safely: a correct deferred-tax answer needs a tax treatment of the $480 issue premium that the task never states (taxed at issue with a reversing DTA, or permanent), and either choice rewrites the whole deferred-tax block and GAAP tax rows 27-29, not a single wrong value
- [F5](../findings.json): Golden tax schedule leaves an unsupported deferred tax liability after the bond is extinguished
  - Reason: duplicate-of:F2
