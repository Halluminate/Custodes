# Changes: FINCH task-157

Fix summary (from the fix record):

graderGuidance: XNPV5 values within 0.5% of the reference are accepted, since the payment-date convention is not stated.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Undisclosed and counter-intuitive XNPV5 calculation convention in B55, B68, and B81 due to stripped formulas in Q1 reference cells B41:B42
  - Change: graderGuidance: one sentence added after the first paragraph: accept XNPV5 values in B55, B68 and B81 within 0.5% of the reference, because the workbook does not state the payment-date convention behind Q1's XNPV figures (covers 1st-of-month vs month-end dating, -0.41%; methods that are not monthly XNPV, e.g. annual lumps -2.6%, still fail).
- other finding, major, not in findings.json: The XNPV method is undocumented: the GT values are hardcoded and the workbook has no date schedule
  - Change: graderGuidance: one sentence added after the first paragraph: accept XNPV5 values in B55, B68 and B81 within 0.5% of the reference, because the workbook does not state the payment-date convention behind Q1's XNPV figures (covers 1st-of-month vs month-end dating, -0.41%; methods that are not monthly XNPV, e.g. annual lumps -2.6%, still fail).
- other finding, major, not in findings.json: XNPV examples and reference answers use a valuation date one month later than their labels
  - Change: graderGuidance: one sentence added after the first paragraph: accept XNPV5 values in B55, B68 and B81 within 0.5% of the reference, because the workbook does not state the payment-date convention behind Q1's XNPV figures (covers 1st-of-month vs month-end dating, -0.41%; methods that are not monthly XNPV, e.g. annual lumps -2.6%, still fail).
