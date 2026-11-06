# Changes: SpreadsheetBench 2 financial-model-02_04

Fix summary (from the fix record):

The prompt asked for Prince realization in USD/KG while the sheet and key are INR/KG; the prompt now says INR/KG.

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, major, not in findings.json: Prompt asks for Prince 'Realization (USD/KG)', but the sheet and the answer key are in INR/KG
  - Change: prompt.md: 'calculate Realization (USD/KG) for Prince' -> 'calculate Realization (INR/KG) for Prince', matching the sheet label H22 'Realization (INR/KG)' and the key I22:L22 =I17/I16 (no FX rate exists in the workbook).
- other finding, major, not in findings.json: Requested USD realization conflicts with the workbook and answer key
  - Change: Same prompt change as another finding (not listed).
