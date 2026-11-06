# Changes: SpreadsheetBench 2 financial-model-10_01

Fix summary (from the fix record):

The prompt now names the sensitivity output as value per share and states the table's location and axis values. Full pass: no further change; the major/minor findings are infra or not task defects.

Changed files (in this folder):

- prompt.md

## Fixed

- [F4](../findings.json) (Task Spec): Sensitivity table output is per-share value, but the prompt asks for 'implied equity value'
  - Change: prompt.md: changed "against implied equity value" to "against value per share" (golden G59 = +E48 Value Per Share)
- [F2](../findings.json) (Task Spec): Sensitivity table axis values, center points, and step increments in Valuation!G59:L64 are not specified in the task context
  - Change: prompt.md: added "Build the table in G59:L64 with value per share in G59, terminal growth rates from 0.5% to 2.5% in 0.5% steps across H59:L59, and WACC from 2% below to 2% above the model's WACC in 1% steps down G60:G64." (matches golden H59:L59 = 0.005..0.025 and G60:G64 = E67 -2%..+2% around 0.05227)
- [F1](../findings.json) (Task Spec): Sensitivity axis values are unstated, so other reasonable grids are rejected (multiple_valid_answers_rejected)
  - Change: prompt.md: added "Build the table in G59:L64 with value per share in G59, terminal growth rates from 0.5% to 2.5% in 0.5% steps across H59:L59, and WACC from 2% below to 2% above the model's WACC in 1% steps down G60:G64." (matches golden H59:L59 = 0.005..0.025 and G60:G64 = E67 -2%..+2% around 0.05227)
- [F3](../findings.json) (Task Spec): Sensitivity-table assumptions are missing from the agent-facing task
  - Change: prompt.md: added "Build the table in G59:L64 with value per share in G59, terminal growth rates from 0.5% to 2.5% in 0.5% steps across H59:L59, and WACC from 2% below to 2% above the model's WACC in 1% steps down G60:G64." (matches golden H59:L59 = 0.005..0.025 and G60:G64 = E67 -2%..+2% around 0.05227)
