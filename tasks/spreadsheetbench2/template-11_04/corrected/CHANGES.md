# Changes: SpreadsheetBench 2 template-11_04

Fix summary (from the fix record):

Two valid modelling choices failed the all-or-nothing cell check: showing the DTL line PPA!C18 as +131.6 (subtracted in C19) instead of -131.6, and filling the later-quarter Beginning Balance cells D33:H33 as the prior Ending Balance. Both are now left out of answer_position; C19, C20, C33 and the whole roll-forward stay checked.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells fails all 3 otherwise-correct submissions due to ambiguous sign on PPA!C18
  - Change: answer_position 'PPA'!B2:H37 -> "'PPA'!B2:H17,'PPA'!B18:B18,'PPA'!D18:H18,'PPA'!B19:H32,'PPA'!B33:C33,'PPA'!B34:H37" (drops C18 and D33:H33). Real scorer: golden 1.0; input + key formulas 1.0; input + key with C18=+131.6, C19=...-C18, C33=C18 and D33:H33 rolled forward 1.0 (was 0.0 with 6 errors); untouched input 0.0 (27 errors).
- other finding, major, not in findings.json: Ambiguous sign convention for PPA!C18 (Deferred Tax Liability on FV Adjustments) causes valid models to score 0.0
  - Change: Same answer_position change: C18 is no longer compared, the downstream Fair Value (733.4), Goodwill (1116.6) and DTL Beginning Balance (131.6) still are.
- other finding, major, not in findings.json: The one-line instruction leaves the DTL sign conventions underspecified, and the binary grader accepts only one of them
  - Change: Same answer_position change covers the positive-C18 reading. Keeping the whole DTL balance negative (C33=-131.6, reductions +4.34) still fails, since the input footnote 'Express deductions as negative numbers' asks for negative reductions.
- other finding, major, not in findings.json: The answer key leaves Beginning Balance blank for Q2 Y1 to Q2 Y2 (D33:H33), so filling in the standard roll-forward scores 0
  - Change: Same answer_position change: D33:H33 are no longer regression cells, so either blank (as in the key) or a roll-forward from the prior Ending Balance passes.
