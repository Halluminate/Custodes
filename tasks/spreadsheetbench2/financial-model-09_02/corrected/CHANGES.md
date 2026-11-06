# Changes: SpreadsheetBench 2 financial-model-09_02

Fix summary (from the fix record):

The cell check no longer grades the Valuation data-table grid H60:L64, which the grading recalculation cannot compute, so a correct formula solution saved with openpyxl or LibreOffice can pass.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F1](../findings.json) (Reward): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check strips Valuation!H60:L64 data-table formulas before recalculation and fails valid MCP/openpyxl submissions (Unit 3 false negative)
  - Change: verifications[0].answer_position: 'Valuation'!C3:O96 split into 'Valuation'!C3:O59,'Valuation'!C60:G64,'Valuation'!M60:O64,'Valuation'!C65:O96, dropping the 25 WACC x terminal-growth data-table cells H60:L64 (=TABLE(...)), which the grading recalculation freezes to the output's cache and so cannot reproduce. graderGuidance range text updated to match. Checked locally with the verifier code: the golden workbook re-saved with openpyxl (correct formulas, no caches) went from reg 1.0 / mod 0.7525 (25 H60:L64 errors) to reg 1.0 / mod 1.0; the golden itself still scores 1.0 and the untouched input still fails.
