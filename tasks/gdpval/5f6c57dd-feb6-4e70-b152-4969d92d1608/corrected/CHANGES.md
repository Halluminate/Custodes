# Changes: GDPval 5f6c57dd-feb6-4e70-b152-4969d92d1608

Fix summary (from the fix record):

Rubric COGS/SG&A variance formulas now match the prompt's 'expense increase = negative' convention, and the regional reconciliation items allow for the Corporate unit that belongs to no region.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Grader guidance contradicts itself and the prompt on the variance sign convention for COGS and SG&A expenses
  - Change: grader guidance: the 8 COGS/SG&A variance-formula items now follow the prompt's sign convention: MoM $ = M23 minus M24, MoM % = (M23 − M24) / M23, YoY $ = FY2023 minus FY2024, YoY % = (FY2023 − FY2024) / FY2023 for COGS and SG&A (the $ items add 'an increase shows as negative, per the prompt's sign convention'). Revenue items unchanged.
- other finding, major, not in findings.json: Regional comparison (Component 4) requirement that the sum of Regions A–G equals All-Company totals is mathematically impossible for SG&A, Allocations, and EBITDA due to the 'Corporate' entity in the raw data
  - Change: grader guidance: the two 'sum of Regions A–G equals the all-company totals' items (FY2024, FY2023) now read 'the sum of regional values across Regions A–G, plus any Corporate amounts not assigned to a region, equals the all-company totals', since allocations, G&A Admin and Operations SG&A sit in the Corporate unit (Region = Corporate) in the raw data.
- other finding, major, not in findings.json: The rubric requires regions A–G to sum to the company total, but the data puts all allocations and most G&A/Ops SG&A in a Corporate unit that belongs to no region
  - Change: Same guidance edit as another finding (not listed).
- other finding, major, not in findings.json: Rubric variance formulas for COGS and SG&A conflict with the required sign convention
  - Change: Same guidance edit as another finding (not listed).
- other finding, major, not in findings.json: Expense variance grading formulas contradict the required favorable/unfavorable signs
  - Change: Same guidance edit as another finding (not listed).
