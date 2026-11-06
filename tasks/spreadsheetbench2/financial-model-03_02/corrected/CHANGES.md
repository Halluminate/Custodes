# Changes: SpreadsheetBench 2 financial-model-03_02

Fix summary (from the fix record):

Corrected the answer key's 'one year' ABV Min/Max/Median/Average (Valuation Band S7:S10) to a real trailing year. Both the calendar-year and the 250-observation readings now pass.

Changed files (in this folder):

- reference/gt_03_Banking_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check fails all three valid attempts (score 0.0) due to defective ground-truth formulas in Valuation Band!S7:S10
  - Change: Answer key: 'Valuation Band'!S7:S10 now read =+MIN/MAX/MEDIAN/AVERAGE(D898:D1142), the trailing calendar year 2013-07-24 to 2014-07-24, the same window as Price Chart's 'One year'. Values are 10.5972 / 11.1280 / 10.8626 / 10.8626. The old key used two different ranges of about two years (D663:D1155 and D668:D1142). Nothing references these cells. Locally, the new key passes against itself, and so does an output that uses the last 250 observations (D893:D1142), which is within 0.1%.
- [F3](../findings.json) (Verification): Golden solution has erroneous and inconsistent cell ranges for 'most recent one year' ABV statistics in Valuation Band!S7:S10
  - Change: Answer key: 'Valuation Band'!S7:S10 now read =+MIN/MAX/MEDIAN/AVERAGE(D898:D1142), the trailing calendar year 2013-07-24 to 2014-07-24, the same window as Price Chart's 'One year'. Values are 10.5972 / 11.1280 / 10.8626 / 10.8626. The old key used two different ranges of about two years (D663:D1155 and D668:D1142). Nothing references these cells. Locally, the new key passes against itself, and so does an output that uses the last 250 observations (D893:D1142), which is within 0.1%.
- [F1](../findings.json) (Verification): The answer key's 'one year' ABV statistics cover about two years, and Min uses a different range from the other three
  - Change: Answer key: 'Valuation Band'!S7:S10 now read =+MIN/MAX/MEDIAN/AVERAGE(D898:D1142), the trailing calendar year 2013-07-24 to 2014-07-24, the same window as Price Chart's 'One year'. Values are 10.5972 / 11.1280 / 10.8626 / 10.8626. The old key used two different ranges of about two years (D663:D1155 and D668:D1142). Nothing references these cells. Locally, the new key passes against itself, and so does an output that uses the last 250 observations (D893:D1142), which is within 0.1%.
- [F2](../findings.json) (Verification): The answer key uses almost two years for the requested one-year ABV statistics
  - Change: Answer key: 'Valuation Band'!S7:S10 now read =+MIN/MAX/MEDIAN/AVERAGE(D898:D1142), the trailing calendar year 2013-07-24 to 2014-07-24, the same window as Price Chart's 'One year'. Values are 10.5972 / 11.1280 / 10.8626 / 10.8626. The old key used two different ranges of about two years (D663:D1155 and D668:D1142). Nothing references these cells. Locally, the new key passes against itself, and so does an output that uses the last 250 observations (D893:D1142), which is within 0.1%.
