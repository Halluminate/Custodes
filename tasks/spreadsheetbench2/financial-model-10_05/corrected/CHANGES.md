# Changes: SpreadsheetBench 2 financial-model-10_05

Fix summary (from the fix record):

The prompt limited Net Profit after Minority Interest to forecast years, but the key fills every period. The sentence now says all periods. The Valuation!H60:L64 Excel data table is now left out of the cell check: LibreOffice cannot recalculate it, so a correct output saved with openpyxl or LibreOffice could never match the key's Excel-computed grid. Checked locally: the input with the key's formulas scores 1.0 under the new ranges both as is and re-saved with openpyxl (it scored 0 under the old ranges).

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F5](../findings.json) (Task Spec): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check fails all 3 valid attempts due to prompt vs. ground-truth contradiction on historical Net Profit after Minority Interest (E47:J47)
  - Change: Prompt: 'then calculate Net Profit after Minority Interest for forecast years.' -> 'then calculate Net Profit after Minority Interest for all periods.' (the key fills Financials!E47:O47).
- [F3](../findings.json) (Verification): Contradiction between task instruction ('for forecast years') and ground truth ('for all periods') on Net Profit after Minority Interest
  - Change: Same prompt sentence change as verifier-correctness-0.
- [F1](../findings.json) (Task Spec): Instruction says to calculate Net Profit after Minority Interest for forecast years only, but the answer key also fills the historical years, so following the instruction exactly scores 0
  - Change: Same prompt sentence change as verifier-correctness-0.
- [F4](../findings.json) (Task Spec): Forecast-only net-profit instruction conflicts with required historical answers
  - Change: Same prompt sentence change as verifier-correctness-0.
- [F2](../findings.json) (Reward): Using openpyxl, the workflow the prompt recommends, breaks the Excel data table on the Valuation sheet, so a fully correct answer still scores 0
  - Change: verify_spreadsheetbench2_cells answer_position: 'Valuation'!C3:O95 split into 'Valuation'!C3:O59,'Valuation'!C60:G64,'Valuation'!M60:O64,'Valuation'!C65:O95, which skips only the data-table grid H60:L64. graderGuidance updated to list the same ranges and say why the grid is skipped.
