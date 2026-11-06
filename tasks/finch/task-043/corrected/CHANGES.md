# Changes: FINCH task-043

Fix summary (from the fix record):

The golden XNPV5 values were discounted to the first payment date (1/31/1997, 1/31/2001) instead of the 12/31/1996 and 12/31/2000 valuation dates, and the monthly month-end convention was never stated. The two GT values are recomputed to the stated dates, and the prompt's XNPV sentence now names the convention.

Changed files (in this folder):

- prompt.md
- reference/gt_43_ref_0.xlsx

## Fixed

- [F1](../findings.json) (Verification): Ground truth for XNPV5 at 12/31/1996 (B41) and 12/31/2000 (B42) is hardcoded from an undisclosed monthly schedule and discounts to 1/31/1997 and 1/31/2001 instead of 12/31/1996 and 12/31/2000
  - Change: gt_43_ref_0.xlsx 'Damage Calculations'!B41: 586,133,469.49 -> 583,709,662.01 and B42: 548,419,739.24 -> 546,151,887.40 (hardcoded values, as before). New values are XNPV at 5% (actual/365) of the row-39 monthly payments at month-ends Jan 1997 (Jan 2001) to Dec 2019, discounted to 12/31/1996 and 12/31/2000. The old values were reproduced exactly as the same flows discounted to the first payment date. No other cell changes and nothing references B41/B42. prompt.md: 'Finally, provide the equity present value (XNPV5) as of 12/31/1996 and 12/31/2000.' -> 'Finally, provide the equity present value (XNPV5) as of 12/31/1996 and 12/31/2000, discounting each Monthly Capacity Payment at 5% from its month-end date back to the valuation date.' (states the monthly month-end convention that the workbook does not reveal).
- [F2](../findings.json) (Verification): GT XNPV values are discounted to the first payment date, not to the 12/31/1996 and 12/31/2000 dates the task asks for
  - Change: gt_43_ref_0.xlsx 'Damage Calculations'!B41: 586,133,469.49 -> 583,709,662.01 and B42: 548,419,739.24 -> 546,151,887.40 (hardcoded values, as before). New values are XNPV at 5% (actual/365) of the row-39 monthly payments at month-ends Jan 1997 (Jan 2001) to Dec 2019, discounted to 12/31/1996 and 12/31/2000. The old values were reproduced exactly as the same flows discounted to the first payment date. No other cell changes and nothing references B41/B42.
