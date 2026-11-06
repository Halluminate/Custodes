# Changes: SpreadsheetBench 2 template-14_01

Fix summary (from the fix record):

Clarified the Stabilized Year 1 NOI basis with one prompt sentence, and took the sign-ambiguous Vacancy Loss row out of answer_position (EGI still graded).

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Undisclosed model conventions and unreferenced assumption in ground truth (Stabilized Year 1 NOI, Property Tax Rate C7 vs C27, Year 1 growth timing, CapEx Reserve inclusion in NOI)
  - Change: Added one prompt sentence after the instruction: 'Base the Stabilized Year 1 NOI on the baseline operating data, before CapEx reserves.' It names the basis the answer key already uses without giving the formula. GT unchanged.
- other finding, major, not in findings.json: The answer key's 'Stabilized Year 1 NOI' (C32) does not match its own projected Year 1 NOI (D60), and the purchase price and every return figure are built on it
  - Change: Added one prompt sentence after the instruction: 'Base the Stabilized Year 1 NOI on the baseline operating data, before CapEx reserves.' It names the basis the answer key already uses without giving the formula. GT unchanged.
- other finding, major, not in findings.json: Acquisition NOI and projected Year 1 NOI use conflicting definitions
  - Change: Added one prompt sentence after the instruction: 'Base the Stabilized Year 1 NOI on the baseline operating data, before CapEx reserves.' It names the basis the answer key already uses without giving the formula. GT unchanged.
- other finding, major, not in findings.json: Undisclosed sign convention for Vacancy Loss (D50:M50) and Acquisition Cost (C62)
  - Change: answer_position now leaves out D50:M50 ('DCF_Analysis'!B2:M49,B50:C50,B51:M65). EGI D51:M51 and everything after it are still compared, so the vacancy amount is still graded through EGI. Real scorer: golden 1.0/1.0, positive-vacancy variant 1.0/1.0 (was mod 0.9242), untouched input mod 0.0 (fails).
