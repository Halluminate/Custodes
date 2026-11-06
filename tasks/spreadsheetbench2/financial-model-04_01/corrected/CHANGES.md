# Changes: SpreadsheetBench 2 financial-model-04_01

Fix summary (from the fix record):

Disclosed the undocumented -1/-2 day inventory step-downs in one prompt sentence, and removed the never-requested pasted sensitivity grid Valuation!H60:L64 from the graded range. Full pass: undefined CAGR cells (sign change or zero/blank endpoint) removed from answer_position.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F5](../findings.json) (Task Spec): Undisclosed forecast step-down assumptions (-1 vs. -2 days) in Average Days Inventory (Assumptions!K141:O141)
  - Change: Prompt: added one sentence after 'In the Assumptions sheet, calculate Average Days Inventory and derive forecast inventory balances.' stating the forecast rule the key uses (prior-two-year average less 1 day for the first three forecast years, less 2 days for the last two), matching GT Assumptions!K141:O141.
- [F3](../findings.json) (Task Spec): Forecast inventory days use hardcoded plugs (-1, -1, -1, -2, -2) that no source discloses, and only that exact sequence passes
  - Change: Prompt: added one sentence after 'In the Assumptions sheet, calculate Average Days Inventory and derive forecast inventory balances.' stating the forecast rule the key uses (prior-two-year average less 1 day for the first three forecast years, less 2 days for the last two), matching GT Assumptions!K141:O141.
- [F6](../findings.json) (Task Spec): Required inventory forecast reductions are not provided
  - Change: Prompt: added one sentence after 'In the Assumptions sheet, calculate Average Days Inventory and derive forecast inventory balances.' stating the forecast rule the key uses (prior-two-year average less 1 day for the first three forecast years, less 2 days for the last two), matching GT Assumptions!K141:O141.
- [F2](../findings.json) (Task Spec): Undisclosed requirement to populate hardcoded DCF sensitivity table values (Valuation!H60:L64)
  - Change: answer_position: 'Valuation'!B2:O99 split to leave out the pasted WACC x terminal-growth grid Valuation!H60:L64 (nothing depends on it). The instruction never asks for it and the prompt forbids changing populated cells, so it is no longer graded.
- [F1](../findings.json) (Verification): The grader requires the WACC × terminal-growth sensitivity table (Valuation!H60:L64), which the instruction never asks for and the 'do not alter cells with values' rule forbids
  - Change: answer_position: 'Valuation'!B2:O99 split to leave out the pasted WACC x terminal-growth grid Valuation!H60:L64 (nothing depends on it). The instruction never asks for it and the prompt forbids changing populated cells, so it is no longer graded.
- [F4](../findings.json) (Task Spec): Grader requires overwriting a populated sensitivity table outside the requested edits
  - Change: answer_position: 'Valuation'!B2:O99 split to leave out the pasted WACC x terminal-growth grid Valuation!H60:L64 (nothing depends on it). The instruction never asks for it and the prompt forbids changing populated cells, so it is no longer graded.
- other finding, major, not in findings.json: Ambiguous specification of 'each relevant metric' for CAGR in Financials (Financials!Q5:R131) and erratic ground-truth formulas for negative/zero values
  - Change: answer_position: 'Financials'!B2:AH133 split to leave out the 14 CAGR cells with no defined CAGR (sign change between endpoints or a zero/blank endpoint): Q100,R100,Q112,R112,Q117,Q129 (golden holds LibreOffice odd-root values like -1.695 that Excel shows as #NUM!) and Q31,R31,Q74,R74,Q80,R80,R57,R126 (golden 'NA' text, where 'NM', blank, -100% etc. are equally valid). Every CAGR with same-sign nonzero endpoints stays graded. Local SB2 scorer: golden PASS, untouched input FAIL (mod 0.0), golden with those 14 cells set to 'NM' PASS. graderGuidance carries the new range list (also covers the earlier Valuation split).
- other finding, major, not in findings.json: The ask for 'CAGR for each relevant metric' leaves open which blank rows to fill, and the GT's choices follow no stated rule
  - Change: answer_position: 'Financials'!B2:AH133 split to leave out the 14 CAGR cells with no defined CAGR (sign change between endpoints or a zero/blank endpoint): Q100,R100,Q112,R112,Q117,Q129 (golden holds LibreOffice odd-root values like -1.695 that Excel shows as #NUM!) and Q31,R31,Q74,R74,Q80,R80,R57,R126 (golden 'NA' text, where 'NM', blank, -100% etc. are equally valid). Every CAGR with same-sign nonzero endpoints stays graded. Local SB2 scorer: golden PASS, untouched input FAIL (mod 0.0), golden with those 14 cells set to 'NM' PASS. graderGuidance carries the new range list (also covers the earlier Valuation split).
