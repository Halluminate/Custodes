# Changes: FINCH task-151

Changed files (in this folder):

- grader_guidance.md
- reference/gt_151_ref_0.xlsx

## Fixed

- other finding, major, not in findings.json: Ground truth gt_151_ref_0.xlsx has inconsistent EBIT formulas in ENA Row 62 ('Upstream Products') and Column Q ('2002 Plan'), causing vertical and horizontal 2002 Plan EBIT totals to disagree (1560.5 vs. 1543.6)
  - Change: Grader guidance: task note accepts row-62 EBIT computed either from the subtotal row's own Margin-Capital-Direct or as the sum of line-item EBITs, with the totals that follow (2002 EBIT 1,560.5 or 1,543.6). gt_151_ref_0.xlsx ENA Q95:Q108, Q111:Q115, Q120:Q128 formulas changed from =N-O-P to =M-N-O (cached values identical, no recalculation needed).
- other finding, major, not in findings.json: Ground truth calculates the Upstream Products subtotal three different ways, so the 2002 Plan EBIT total does not tie to Margin − Capital − Direct
  - Change: Same task note on row 62 and the 2002 EBIT totals.
- other finding, minor, not in findings.json: GT 2002 Plan EBIT formula breaks pattern in rows 95–131 and leaves out the Allocated column
  - Change: gt_151_ref_0.xlsx ENA: shared-formula masters Q95 and Q120 and Q111:Q115 changed from N-O-P to M-N-O (Margin - Capital - Direct), at XML level. Every cached value and all other cells unchanged.
- other finding, major, not in findings.json: Inconsistent upstream subtotal creates conflicting 2002 EBIT answers
  - Change: Same task note on row 62 and the 2002 EBIT totals.
