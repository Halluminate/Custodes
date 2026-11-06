# Changes: SpreadsheetBench 2 financial-model-05_05

Fix summary (from the fix record):

Added one sentence to the instruction giving the starting monthly salaries the answer key uses in 'Workings Cost Sheet'!N68:N73, which appear nowhere in the input.

Changed files (in this folder):

- prompt.md

## Fixed

- [F2](../findings.json) (Environment & Infra): Undisclosed base monthly salary assumptions required in 'Workings Cost Sheet'!N68:N73 make 65.65% of modification cells impossible to derive
  - Change: prompt.md: after 'calculate salary per month with annual increases for all designations.' added: 'Start the monthly salaries in column N at 200,000, 150,000, 100,000 and 50,000 for Designated Partners, Head of Operations, Analyst and Associate, scaled to the sheet's units as =200000/10^5 and so on, and at 0 for General Support and Senior Associate.' This matches golden N68:N73 (2.0, 1.5, 1.0, 0.5, 0, 0).
- [F3](../findings.json) (Environment & Infra): Starting monthly salaries in the answer key appear nowhere in the input or the prompt, so the task cannot be passed
  - Change: prompt.md: after 'calculate salary per month with annual increases for all designations.' added: 'Start the monthly salaries in column N at 200,000, 150,000, 100,000 and 50,000 for Designated Partners, Head of Operations, Analyst and Associate, scaled to the sheet's units as =200000/10^5 and so on, and at 0 for General Support and Senior Associate.' This matches golden N68:N73 (2.0, 1.5, 1.0, 0.5, 0, 0).
- [F1](../findings.json) (Environment & Infra): Required starting salary assumptions are missing
  - Change: prompt.md: after 'calculate salary per month with annual increases for all designations.' added: 'Start the monthly salaries in column N at 200,000, 150,000, 100,000 and 50,000 for Designated Partners, Head of Operations, Analyst and Associate, scaled to the sheet's units as =200000/10^5 and so on, and at 0 for General Support and Senior Associate.' This matches golden N68:N73 (2.0, 1.5, 1.0, 0.5, 0, 0).
