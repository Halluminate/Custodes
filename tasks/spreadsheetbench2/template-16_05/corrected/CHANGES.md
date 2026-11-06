# Changes: SpreadsheetBench 2 template-16_05

Fix summary (from the fix record):

Column-H revenue $/SF cells H11:H27 and the NOI cell H45 left out of grading; the valuation (column I) and $/Unit expenses H31:H43 are still checked.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Undisclosed monthly $/SF convention and SF denominator in DirectCap!H11:H27
  - Change: answer_position 'DirectCap'!B2:P49,... -> "'DirectCap'!B2:G49,'DirectCap'!H2:H10,'DirectCap'!H28:H44,'DirectCap'!H46:H49,'DirectCap'!I2:P49,'RentRoll'!A1:P12" (drops H11:H27 and H45). Real scorer: golden 1.0/1.0; golden with annual $/SF (I/RentRoll!D12) and H45 = NOI per unit 1.0/1.0 (was mod 0.7347 = fail); untouched input fails (mod 0.0). graderGuidance updated.
- other finding, major, not in findings.json: Graded cell H45 holds an NOI margin, but the column headers say it should be a $/SF or $/Unit figure
  - Change: answer_position 'DirectCap'!B2:P49,... -> "'DirectCap'!B2:G49,'DirectCap'!H2:H10,'DirectCap'!H28:H44,'DirectCap'!H46:H49,'DirectCap'!I2:P49,'RentRoll'!A1:P12" (drops H11:H27 and H45). Real scorer: golden 1.0/1.0; golden with annual $/SF (I/RentRoll!D12) and H45 = NOI per unit 1.0/1.0 (was mod 0.7347 = fail); untouched input fails (mod 0.0). graderGuidance updated.
- other finding, major, not in findings.json: Pass/fail depends on optional column-H metrics, and the time basis for $/SF is never stated
  - Change: answer_position 'DirectCap'!B2:P49,... -> "'DirectCap'!B2:G49,'DirectCap'!H2:H10,'DirectCap'!H28:H44,'DirectCap'!H46:H49,'DirectCap'!I2:P49,'RentRoll'!A1:P12" (drops H11:H27 and H45). Real scorer: golden 1.0/1.0; golden with annual $/SF (I/RentRoll!D12) and H45 = NOI per unit 1.0/1.0 (was mod 0.7347 = fail); untouched input fails (mod 0.0). graderGuidance updated.
