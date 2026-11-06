# Changes: SpreadsheetBench 2 financial-model-06_03

Fix summary (from the fix record):

The key computed month-over-month growth in the monthly revenue-growth cells although the prompt asks for YoY; those cells are now YoY, with NM for the first 12 months. Full pass: 'Ratio Analysis'!F7 (FY2026 growth over a lakhs-scaled FY2025 base, no single defensible value) is left out of answer_position.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_06_DigiMark_golden.xlsx

## Fixed

- [F1](../findings.json) (Verification): The answer key grades month-over-month growth instead of the requested YoY growth
  - Change: gt_06_DigiMark_golden.xlsx 'Ratio Analysis' row 7 monthly cells: M7:W7 (May-25 to Mar-26, no prior-year month) set to 'NM' like L7; X7:BS7 now compare with the same month a year earlier, e.g. X7 ='Income Statement'!Y19/'Income Statement'!M19-1 (0.3174, was 0.1536 MoM). Annual cells F7:J7 untouched; caches recalculated, no other cell changed, GT scores 1.0 on its verifier.
- other finding, major, not in findings.json: Ground truth's FY2026 revenue growth is a nonsensical 3,176,583% because it divides by FY2025 revenue stored in lakhs
  - Change: verifications[0].parameters.answer_position: 'Ratio Analysis'!B2:BS22 split into B2:BS6, B7:E7, G7:BS7, B8:BS22, so only 'Ratio Analysis'!F7 (FY2026 YoY growth, key 31765.83 from dividing USD revenue by the lakhs-scaled FY2025 figure; NM and the rescaled -68% are equally defensible) is no longer compared. id/name/function/weight unchanged; graderGuidance range list and a note updated to match. Local SB2 grade: golden 1.0/1.0 under old and new ranges; golden with F7='NM' 0.0 before (mod 0.9953, F7 only) and 1.0 after.
