# Changes: SpreadsheetBench 2 financial-model-04_04

Fix summary (from the fix record):

The key fills six Valuation Blended Price cells the instruction never asked for; one prompt sentence now asks for them.

Changed files (in this folder):

- prompt.md

## Fixed

- [F4](../findings.json) (Task Spec): SpreadsheetBench 2 official cell check: Verifier fails all units (score=0.0) because 81 of 190 graded modification cells depend on uninstructed edits in the Valuation sheet
  - Change: Prompt: added one sentence to the instruction list: 'In the Valuation sheet, complete the Blended Price table (average price, current price, consensus TP, upside/(downside) and the two variances).' This asks for the six cells the key fills (Valuation!D95, G95, D97, G97, D99, G99) that drive Final Output!D8/D9 and ~120 downstream graded cells.
- [F2](../findings.json) (Task Spec): Prompt instructions mismatch the input/golden workbook diff: Valuation sheet Blended Price table is omitted from instructions while Ratio Analysis ratios are already pre-filled
  - Change: Prompt: added one sentence to the instruction list: 'In the Valuation sheet, complete the Blended Price table (average price, current price, consensus TP, upside/(downside) and the two variances).' This asks for the six cells the key fills (Valuation!D95, G95, D97, G97, D99, G99) that drive Final Output!D8/D9 and ~120 downstream graded cells.
- [F1](../findings.json) (Task Spec): Ground truth fills six Valuation cells the instruction never asks for, and the all-or-nothing verifier grades them plus about 120 cells that depend on them
  - Change: Prompt: added one sentence to the instruction list: 'In the Valuation sheet, complete the Blended Price table (average price, current price, consensus TP, upside/(downside) and the two variances).' This asks for the six cells the key fills (Valuation!D95, G95, D97, G97, D99, G99) that drive Final Output!D8/D9 and ~120 downstream graded cells.
- [F3](../findings.json) (Verification): Grader requires six valuation outputs absent from the task instructions
  - Change: Prompt: added one sentence to the instruction list: 'In the Valuation sheet, complete the Blended Price table (average price, current price, consensus TP, upside/(downside) and the two variances).' This asks for the six cells the key fills (Valuation!D95, G95, D97, G97, D99, G99) that drive Final Output!D8/D9 and ~120 downstream graded cells.
- other finding, major, not in findings.json: Ambiguous D&A forecast methodology in Assumptions!K131:O131 where the golden workbook links to Cash Flow Statement instead of using the adjacent Assumptions driver row
  - Change: Prompt: changed 'then calculate Depreciation and Amortization for the forecast period.' to 'then calculate Depreciation and Amortization for the forecast period so that it agrees with the D&A used in the Financials sheet.' This matches the key (Assumptions!K131:O131 =Financials!K111:O111) and removes the competing row-133 reading.
- other finding, major, not in findings.json: Forecast depreciation assumptions contradict the amounts required by the golden workbook
  - Change: Same prompt change as another finding (not listed) (D&A must agree with the Financials sheet).
- other finding, major, not in findings.json: The two Ratio Analysis tasks are already done in the input, so the instruction asks for work the GT does not contain
  - Change: Prompt: removed the sentence 'In the Ratio Analysis sheet, calculate Liabilities/Assets for all periods, then calculate Debt/Total Capital for all periods.' Both rows are already complete in the input and unchanged in the key (regression cells only), and the key's added Valuation work is already asked for by the critical-pass sentence. Grading is unchanged.
- other finding, major, not in findings.json: Pre-existing Debt/Total Capital and Debt/Equity formulas are wrong, and a correct recalculation would be penalized as a regression
  - Change: Same prompt change as another finding (not listed): the agent is no longer asked to recalculate Debt/Total Capital, so the pre-existing row 26 is simply preserved as the key expects.
- other finding, major, not in findings.json: Seeded leverage ratios use total assets instead of equity
  - Change: Same prompt change as another finding (not listed).
