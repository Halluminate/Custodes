# Changes: SpreadsheetBench 2 financial-model-08_03

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Debt to Equity definition is ambiguous when Balance Sheet contains both Long Term Debt and Working Capital Loan, and adjacent Debt to EBITDA includes both
  - Change: prompt.md: changed the sentence 'In the Ratio Analysis tab, for all years calculate Debt to Equity.' to 'In the Ratio Analysis tab, for all years calculate Debt to Equity as Long Term Debt divided by total shareholders' equity.' (the key's definition). Key and grading unchanged.
- other finding, major, not in findings.json: Debt to Equity has a reasonable alternative definition that the binary grader rejects
  - Change: prompt.md: changed the sentence 'In the Ratio Analysis tab, for all years calculate Debt to Equity.' to 'In the Ratio Analysis tab, for all years calculate Debt to Equity as Long Term Debt divided by total shareholders' equity.' (the key's definition). Key and grading unchanged.
- other finding, major, not in findings.json: Debt-to-equity answer key excludes working-capital debt
  - Change: prompt.md: changed the sentence 'In the Ratio Analysis tab, for all years calculate Debt to Equity.' to 'In the Ratio Analysis tab, for all years calculate Debt to Equity as Long Term Debt divided by total shareholders' equity.' (the key's definition). Key and grading unchanged.
- other finding, minor, not in findings.json: All-or-nothing grading includes a floating-point-noise cell compared on relative tolerance
  - Change: verifications[0].parameters.answer_position: 'Funding Schedule'!B2:T195 split into B2:T104, B105:H105, J105:T105, B106:T195 so the float-residue cell I105 is no longer compared; grader guidance range text updated. Checked with the real SB2 scorer (forced LibreOffice recalc, new answer_position): golden PASS (reg 1.0, mod 1.0), input plus the key's 215 changed cells (formulas only, no cached values) PASS; the untouched input still fails (2,200 modification cells blank).
