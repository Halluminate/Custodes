# Changes: SpreadsheetBench 2 template-03_03

Fix summary (from the fix record):

The answer key entered 'Less: NCI Portion' as +43.75, against the sheet's footnote 'Express deductions as negative numbers'. It is now -43.75. The NCI roll-forward formula is adjusted so the balance sheet stays the same. Full pass: answer_position no longer grades the unstyled standalone Acquirer/Target subtotals (C16:D16, C28:D30) or the consolidated dividends cell F34, which a correct model may fill or leave blank.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_03_03_golden.xlsx

## Fixed

- [F2](../findings.json) (Verification): Contradictory sign convention on 'Less: NCI Portion' (E31, F31) between worksheet footnote B59 and ground truth
  - Change: gt_03_03_golden.xlsx Consolidation!E31 changed from =D30*(1-C8) to =-D30*(1-C8) (cached -43.75). F31 =E31 now caches -43.75. D54 changed from =C54+E31+F41 to =C54-E31+F41 so NCI stays 83.75 and the check rows stay 0. No other cached value changed. Income tax lines stay positive, like the pre-filled positive Operating Expenses in the input. The patched GT, recalculated in LibreOffice, scores reg 1.0 / mod 1.0 locally.
- [F3](../findings.json) (Verification): Answer key enters 'Less: NCI Portion' as a positive number, which contradicts the sheet's own 'deductions as negative numbers' footnote
  - Change: Same GT fix: Consolidation!E31/F31 = -43.75, D54 =C54-E31+F41.
- [F1](../findings.json) (Verification): Answer key contradicts the workbook's required deduction signs
  - Change: Same GT fix: Consolidation!E31/F31 = -43.75, D54 =C54-E31+F41.
- other finding, major, not in findings.json: Task prompt and cell styling omit standalone Acquirer and Target subtotals (C16, D16, C28:D30) that the verifier requires
  - Change: verifications[0].parameters.answer_position: 'Consolidation'!B2:G59 -> 'Consolidation'!B2:B59,'Consolidation'!C2:D15,'Consolidation'!C17:D27,'Consolidation'!C31:D59,'Consolidation'!E2:E59,'Consolidation'!F2:F33,'Consolidation'!F35:F59,'Consolidation'!G2:G59 (drops C16:D16 and C28:D30, unstyled standalone subtotals the key fills but the template never marks, and F34, which the key leaves blank though filling 200 is correct). graderGuidance updated. Local check with the verifier's forced recalc: patched GT PASS 1.0/1.0; GT with C16:D16, C21:D21, C28:D30 blank and F34 =C34 PASS 1.0/1.0 (FAIL mod 0.81 under the old range); untouched input FAIL.
- other finding, major, not in findings.json: One-line instruction does not say which cells to fill, but the binary grader requires an exact set of filled and blank cells
  - Change: verifications[0].parameters.answer_position: 'Consolidation'!B2:G59 -> 'Consolidation'!B2:B59,'Consolidation'!C2:D15,'Consolidation'!C17:D27,'Consolidation'!C31:D59,'Consolidation'!E2:E59,'Consolidation'!F2:F33,'Consolidation'!F35:F59,'Consolidation'!G2:G59 (drops C16:D16 and C28:D30, unstyled standalone subtotals the key fills but the template never marks, and F34, which the key leaves blank though filling 200 is correct). graderGuidance updated. Local check with the verifier's forced recalc: patched GT PASS 1.0/1.0; GT with C16:D16, C21:D21, C28:D30 blank and F34 =C34 PASS 1.0/1.0 (FAIL mod 0.81 under the old range); untouched input FAIL.
