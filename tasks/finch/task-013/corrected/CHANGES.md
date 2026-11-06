# Changes: FINCH task-013

Fix summary (from the fix record):

Full pass: the judge now accepts simple as well as compound annualization in row 12, and a return that adds back in-hold coupons (same values at the default 0.5-year hold).

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Annualization method for the holding-period return is not specified, so a valid simple-annualized answer would be marked wrong
  - Change: grader_guidance.md: added one sentence after the opening paragraph: 'For the Annualized Holding Period Return in row 12, accept simple annualization ((Final Full Price / Initial Full Price - 1) / holding period) as well as the reference's compound form, and accept a return that also adds back coupons received during the holding period (none fall inside the default 0.5-year hold).'
- other finding, minor, not in findings.json: Ground-truth return ignores coupons received during the holding period, so it is wrong when the holding period is over 1 year
  - Change: grader_guidance.md: added one sentence after the opening paragraph: 'For the Annualized Holding Period Return in row 12, accept simple annualization ((Final Full Price / Initial Full Price - 1) / holding period) as well as the reference's compound form, and accept a return that also adds back coupons received during the holding period (none fall inside the default 0.5-year hold).'
