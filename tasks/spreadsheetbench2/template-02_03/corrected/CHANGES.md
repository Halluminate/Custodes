# Changes: SpreadsheetBench 2 template-02_03

Fix summary (from the fix record):

Prompt now states the key's treatment of retained operating cash; Total Debt Repayment C31:F31 left out of grading so either sign passes (Remaining Cash row 32 is still checked).

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Ambiguous treatment of retained Required Operating Cash in Remaining Cash After Debt Service (C32:F32) and Beginning Cash roll-forward (D8:F8)
  - Change: problemStatement: appended one sentence to the Instruction line: 'Treat the retained Required Operating Cash as used in the quarter, so it is excluded from Remaining Cash After Debt Service and does not roll forward into the next quarter's Beginning Cash.' (the key's reading: C32 =C11-C30-C31 = 0 and D8 rolls only that remainder). Golden and verifier unchanged for this.
- other finding, major, not in findings.json: Retained operating cash disappears from the waterfall instead of rolling forward (alternative reading penalized by an all-or-nothing check)
  - Change: problemStatement: appended one sentence to the Instruction line: 'Treat the retained Required Operating Cash as used in the quarter, so it is excluded from Remaining Cash After Debt Service and does not roll forward into the next quarter's Beginning Cash.' (the key's reading: C32 =C11-C30-C31 = 0 and D8 rolls only that remainder). Golden and verifier unchanged for this.
- other finding, major, not in findings.json: Undisclosed mixed sign convention across debt repayment and interest expense rows in DebtWaterfall
  - Change: answer_position 'DebtWaterfall'!B2:F32,... -> "'DebtWaterfall'!B2:F30,'DebtWaterfall'!B31,'DebtWaterfall'!B32:F32,'SharedData'!B2:B12" (drops C31:F31 only). Real scorer: golden 1.0/1.0; golden with negative Total Debt Repayment (=C15+C16+C23+C24, C32 =C11-C30+C31) 1.0/1.0 (was mod 0.8947 = fail); untouched input fails (mod 0.0). graderGuidance updated.
- other finding, major, not in findings.json: Sign convention for derived rows is unstated, but the values-mode check penalizes the opposite sign
  - Change: answer_position 'DebtWaterfall'!B2:F32,... -> "'DebtWaterfall'!B2:F30,'DebtWaterfall'!B31,'DebtWaterfall'!B32:F32,'SharedData'!B2:B12" (drops C31:F31 only). Real scorer: golden 1.0/1.0; golden with negative Total Debt Repayment (=C15+C16+C23+C24, C32 =C11-C30+C31) 1.0/1.0 (was mod 0.8947 = fail); untouched input fails (mod 0.0). graderGuidance updated.
