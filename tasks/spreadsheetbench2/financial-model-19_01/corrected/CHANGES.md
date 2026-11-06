# Changes: SpreadsheetBench 2 financial-model-19_01

Fix summary (from the fix record):

Full pass: the Forecast CAGR period convention is now stated in the prompt; other findings are false positives.

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, major, not in findings.json: SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check fails all 3 valid runs (score=0) due to unstated 4-period FY26E–FY30E Forecast CAGR convention at IS!O8
  - Change: prompt.md: 'Calculate Historical CAGR and Forecast CAGR for Total Revenue.' -> 'Calculate Historical CAGR (FY20A to FY25A) and Forecast CAGR (FY26E to FY30E) for Total Revenue, each measured from the first to the last year of its period.'. States the key's period convention (IS!N8 =(H8/C8)^(1/5)-1, IS!O8 =(M8/I8)^(1/4)-1); answer key and grading unchanged.
- other finding, major, not in findings.json: Ambiguous 'Forecast CAGR' definition in IS!O8 (FY26E–FY30E 4-year CAGR vs. FY25A–FY30E 5-year CAGR)
  - Change: Same prompt sentence as verifier-correctness-0.
- other finding, major, not in findings.json: Forecast CAGR period convention is unstated and inconsistent with Historical CAGR; the all-or-nothing grader rejects the common FY25A→FY30E reading
  - Change: Same prompt sentence as verifier-correctness-0.
