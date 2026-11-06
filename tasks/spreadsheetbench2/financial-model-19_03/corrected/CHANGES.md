# Changes: SpreadsheetBench 2 financial-model-19_03

Fix summary (from the fix record):

Full pass: the prompt now defines Quick Ratio as the golden computes it (current assets less inventories over current liabilities).

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, major, not in findings.json: Quick Ratio definition is not stated, yet the all-or-nothing grader accepts only (Current Assets − Inventories)/Current Liabilities
  - Change: Prompt: the sentence 'In the Ratio Analysis sheet, calculate Quick Ratio for FY20A–FY30E.' now ends 'as Total Current Assets less Inventories, divided by Total Current Liabilities.', the definition the golden uses in Ratio Analysis!C18:M18 =(BS!x19-BS!x14)/BS!x40. Answer key and grading unchanged.
