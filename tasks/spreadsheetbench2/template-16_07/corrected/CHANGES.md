# Changes: SpreadsheetBench 2 template-16_07

Fix summary (from the fix record):

Full pass: blank-in-key $/Unit/Yr and valuation cells C42/C44/C45/C51/C52 removed from the cell check.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: SpreadsheetBench 2 official cell check: SpreadsheetBench 2 official cell check fails complete, mathematically accurate models for populating $/Unit/Yr cells C42, C44, and C45
  - Change: verifications[0].parameters.answer_position: 'RentRoll'!B2:J20,'ValuationModel'!B2:J52 -> 'RentRoll'!B2:J20,'ValuationModel'!B2:J41,'ValuationModel'!B42,'ValuationModel'!D42:J42,'ValuationModel'!B43:J43,'ValuationModel'!B44:B45,'ValuationModel'!D44:J45,'ValuationModel'!B46:J50,'ValuationModel'!B51:B52,'ValuationModel'!D51:J52 (drops ValuationModel C42, C44, C45, C51, C52: blank in the key, but they sit under the '$/Unit/Yr' header (C31) or in the header-less VALUATION block, so filling them with per-unit figures is an equally valid layout). Every filled cell stays graded. graderGuidance updated with the new range. Local SB2 scorer: golden 1.0 (old and new), untouched input 0.0, golden plus C42=8004/C44/C45/C51/C52 filled 0.0 under old range (reg 0.9902) and 1.0 under new.
- other finding, major, not in findings.json: Undisclosed column placement and omission constraints for Fixed Expenses, Total Operating Expenses, and Valuation rows
  - Change: Same answer_position change as verifier-correctness-0.
- other finding, major, not in findings.json: One-line vague instruction is graded all-or-nothing on ~130 cells, and several unstated conventions decide pass or fail
  - Change: Same answer_position change as verifier-correctness-0 (its point d). Points a-c and e follow the labels and layout and were left as is.
