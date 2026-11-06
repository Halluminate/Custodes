# Changes: SpreadsheetBench 2 financial-model-12_02

Fix summary (from the fix record):

The prompt asked for depreciation 'at 5%' with no base, but the answer key applies the row-12 Depreciation % (4.815%, displayed as 5%) to Opening Bal. plus Capex. Reworded that one sentence to name the rate cell and the base. Full pass: no task change; the major/minor findings are infra, duplicates, not fixable in the task, or false positives.

Changed files (in this folder):

- prompt.md

## Fixed

- [F1](../findings.json) (Task Spec): Ambiguous and contradictory Depreciation instruction ('at 5%') causes valid interpretations to fail the verifier
  - Change: prompt.md: replaced 'calculate Depreciation of Consolidated PP&E for Mar-26 to Mar-30 at 5%.' with '... by applying the Depreciation % in row 12 (shown as 5%) to Opening Bal. plus Capex.', which matches GT 'Assets Sch.'!I9:M9 =(I7+I8)*I12
- [F2](../findings.json) (Verification): Instruction says 5% depreciation, but the answer key uses the model's 4.815% rate
  - Change: same prompt sentence change: the rate is now the row-12 Depreciation % the answer key uses, not a literal 5%

## Confirmed findings not fixed

- [F3](../findings.json): The instructed 5% depreciation rate conflicts with the answer key
  - Reason: duplicate-of:F2
