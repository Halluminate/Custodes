# Changes: SpreadsheetBench 2 financial-model-09_05

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, major, not in findings.json: Ambiguous Payout Ratio definition (Basic vs. Diluted EPS) causes 11 modification cell failures
  - Change: Prompt: the Payout Ratio sentence now reads "In the Financials sheet, calculate the Payout Ratio for all periods as Reported DPS over Reported EPS - Diluted." (the key's E66:O66 =E65/E63). Answer key unchanged.
- other finding, major, not in findings.json: Payout Ratio answer key accepts only DPS ÷ diluted EPS; the equally standard basic-EPS version fails the all-or-nothing grade
  - Change: Same prompt change as another finding (not listed) (payout ratio basis stated as Reported DPS over Reported EPS - Diluted).
- other finding, major, not in findings.json: Ambiguous Book Value per Share definition (treatment of Minority Interest, Preferred Equity, and Basic vs. Diluted shares) causes modification and regression failures
  - Change: Prompt: the Ratio Analysis sentence now reads "In the Ratio Analysis sheet, calculate Book Value per Share as Total Equity less Minority interest over the basic weighted average shares, then calculate Debt-to-Total Capital." (the key's F31:O31 =(Financials!F101-Financials!F99)/Financials!F59). Answer key unchanged.
- other finding, major, not in findings.json: Book Value per Share answer key relies on unstated choices (minus minority interest, basic shares); reasonable alternatives fail and preferred equity is wrongly left in
  - Change: Same prompt change as another finding (not listed) (BVPS basis stated). The preferred-equity point is within the 1% tolerance (about 0.25%) and needs no key change.
