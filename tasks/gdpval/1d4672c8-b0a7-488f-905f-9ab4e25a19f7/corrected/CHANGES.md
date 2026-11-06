# Changes: GDPval 1d4672c8-b0a7-488f-905f-9ab4e25a19f7

Fix summary (from the fix record):

Grader guidance now tells the grader that the expert's correlation table and PDF are computed on index levels, not returns, so their figures and conclusions are not to be treated as correct; the expert workbook is unchanged.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- [F3](../findings.json) (Verification): Ground truth deliverables fail 11 rubric items (15 of 59 points) and compute correlations on raw index levels instead of monthly returns
  - Change: graderGuidance: added "The expert Correlation Table and PDF compute the coefficients on month-end index levels, not on monthly returns (for example EM vs AC Asia Pacific ex Japan 0.968 and EM Latin America vs World -0.572), so do not treat the expert's figures, or conclusions drawn from them, as correct." The expert workbook is left as it is: refilling it with newly computed coefficients would write a new answer (cannot-fix-safely: would invent content).
- [F2](../findings.json) (Verification): The answer key correlates price levels, not monthly returns, so its whole matrix and all its conclusions are wrong
  - Change: graderGuidance: added "The expert Correlation Table and PDF compute the coefficients on month-end index levels, not on monthly returns (for example EM vs AC Asia Pacific ex Japan 0.968 and EM Latin America vs World -0.572), so do not treat the expert's figures, or conclusions drawn from them, as correct." The expert workbook is left as it is: refilling it with newly computed coefficients would write a new answer (cannot-fix-safely: would invent content).

## Confirmed findings not fixed

- [F1](../findings.json): Problem statement says reference files are on the Desktop, but the Desktop is empty and all data must be scraped live from msci.com
  - Reason: infra
