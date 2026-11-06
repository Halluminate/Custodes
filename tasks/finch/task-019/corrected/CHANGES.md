# Changes: FINCH task-019

Fix summary (from the fix record):

The answer key's Netflix 2021 free cash flow is corrected from +1.59B to -0.13B, and the four cells that depend on it are recomputed. Prompt asks for reported operating profit instead of a non-existent IFRS figure.

Changed files (in this folder):

- prompt.md
- reference/gt_19_ref_0.xlsx

## Fixed

- [F1](../findings.json) (Verification): Answer key has the wrong sign and size for Netflix's 2021 free cash flow, and the error flows into three other sheets
  - Change: gt_19_ref_0.xlsx: Netflix 2021 FCF corrected from 1.59 to -0.13 (10-K: operating cash flow 0.39B less purchases of property and equipment 0.52B) in RawData!F23 (kept the sheet's '–' text style), Sheet2_YoY_Growth!G23; dependent cells Sheet2!H23 -17.62 -> -106.74 and H24 1.89 -> -1346.15 (same signed-division convention the key uses for Amazon), Sheet3_Ranking_By_Year!G11 -> -0.13 (FCF rank 4 unchanged), Sheet4_Five_Year_Summary!E6 18.99 -> 17.27. Sheet5 (2024 only) unaffected.
- [F2](../findings.json) (Verification): Reference incorrectly records Netflix's 2021 free cash flow as positive 1.59 billion
  - Change: Same edit (RawData!F23 and its dependents).
- other finding, major, not in findings.json: The task asks for operating profit 'according to IFRS', but all five companies report under US GAAP
  - Change: prompt: 'Operating profit according to International Financial Reporting Standards (in billions of US dollars)' changed to 'Operating profit as reported in the company's financial statements (in billions of US dollars)'; key unchanged (it already uses reported operating income).
- other finding, major, not in findings.json: Requested IFRS operating profits conflict with the reference's US-GAAP figures
  - Change: Same prompt edit as another finding (not listed).
