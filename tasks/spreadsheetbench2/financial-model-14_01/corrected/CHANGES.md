# Changes: SpreadsheetBench 2 financial-model-14_01

Fix summary (from the fix record):

The prompt asked for EBITDA Margin, which is already filled, while the answer key grades the blank PAT Margin row; the prompt now asks for PAT Margin. The golden also cached ~1e-13 float residue in NCD/TL debt-schedule cells that the relative tolerance rejects; those caches are now exactly 0, and the golden passes its own verifier. Full pass: the Working Capital and CFS-check sentences now describe what the key computes (total working capital movement; closing cash vs Balance sheet cash).

Changed files (in this folder):

- prompt.md
- reference/gt_14_Refinery_golden.xlsx

## Fixed

- [F6](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells is a trivial fail (impossible to pass) due to unrounded float comparison on near-zero debt schedule cells and Excel DATA TABLE stale cache in golden file
  - Change: gt_14_Refinery_golden.xlsx: 4,700 formula cells whose cached value was floating-point residue (0 < |v| < 1e-6; NCD 1,981, TL 2,674, Depn - IT _Current 43, Cash Flow 2, e.g. NCD!AA137 -3.375e-13) now cache exactly 0, formulas and every other cell unchanged (XML <v> edit). Zero triggers the verifier's absolute tolerance, so LibreOffice's own residue (e.g. -3.801e-13) matches. Local grade of the new golden through the real verifier: reg 1.0, mod 1.0 (was mod 0.9531, 98 errors).
- [F5](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: Same GT residue-to-zero edit; golden now scores 1.0.
- [F1](../findings.json) (Reward): The golden workbook fails its own grading after required recalculation
  - Change: Same GT residue-to-zero edit.
- [F2](../findings.json) (Task Spec): Prompt instructs agent to calculate already-populated 'EBITDA Margin' instead of missing 'PAT Margin %' in Profit & Loss sheet
  - Change: prompt.md: 'In the Profit & Loss sheet, calculate EBITDA Margin for Q4 2019-20 through 2026-27.' -> '... calculate PAT Margin for Q4 2019-20 through 2026-27.' Row 37 EBITDA Margin is already filled in the input; the GT fills row 38 PAT Margin J38:R38.
- [F4](../findings.json) (Task Spec): Instruction asks for EBITDA Margin, but that row is already filled; the answer key grades PAT Margin (row 38) instead
  - Change: Same prompt sentence change (EBITDA Margin -> PAT Margin).
- [F3](../findings.json) (Verification): The task requests EBITDA margins but the answer key requires PAT margins
  - Change: Same prompt sentence change (EBITDA Margin -> PAT Margin).
- other finding, minor, not in findings.json: CFS control check target row (Difference vs Check) and formula direction are underspecified
  - Change: prompt.md: 'add a control check validating that closing cash each period matches opening cash in the subsequent period.' -> '... matches the cash balance on the Balance sheet.' (what the key's row 53 Difference = row 50 closing cash - row 52 Balance sheet cash checks).
- other finding, major, not in findings.json: The Working Capital instruction names only receivables, inventory and payables, but the GT uses the movement in total working capital, including other current and non-current items
  - Change: prompt.md: '... based on period-to-period movements in receivables, inventory, and payables.' -> '... based on period-to-period movements in total working capital.' (the key's J32:P32 = J29-I29, row 29 'Working Capital', like the historical D32:G32).
