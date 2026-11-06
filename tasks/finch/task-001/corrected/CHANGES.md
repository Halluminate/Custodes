# Changes: FINCH task-001

Fix summary (from the fix record):

The answer key used signed PHAS formulas or swapped markers for five of the twelve A/B sums, so a literal sum of the tagged cells failed. Those cells in gt_1_ref_0.xlsx now sum exactly the cells tagged A or B, with cached values set and local sheet references instead of the external [1] link.

Changed files (in this folder):

- reference/gt_1_ref_0.xlsx

## Fixed

- [F4](../findings.json) (Task Spec): Undisclosed subtraction conventions in ground truth for 'sum of A' and 'sum of B' (L134, N132, V132) despite positive values in source component columns
  - Change: gt_1_ref_0.xlsx Income Statement: L134 = 'Balance Sheet'!L83+L86 (62,734), N132 = sum of the 11 A-tagged Balance Sheet N cells (208,360), V132 = sum of the 12 A-tagged Income Statement V cells incl. V10 (582,287). V134 (was =N132) now sums its own B-tagged Balance Sheet V cells, value unchanged at 83,606.
- [F1](../findings.json) (Verification): Ground-truth reference gt_1_ref_0.xlsx contains contradictory and erroneous formulas in R132, R134, and V132 (and external workbook links in L132, L134, N132, P132)
  - Change: Same file: R132 = R125 (1,224, tagged A) and R134 = R124 (1,178, tagged B); V132 no longer references A86 and includes V10; L132, N132, P132, L134 now reference the local 'Balance Sheet' sheet instead of '[1]Balance Sheet' (L132 and P132 values unchanged).
- [F5](../findings.json) (Verification): The answer key does not use 'sum of A / sum of B' for several indicators: it applies the original PHAS sign logic, so an agent that literally sums the marked cells fails
  - Change: Same L134, N132, V132 changes: answer key is now the literal sum of the marked cells.
- [F2](../findings.json) (Verification): Occupancy Loss: the GT swaps the A and B values relative to the workbook's own markers
  - Change: R132 = R125 (1,224) and R134 = R124 (1,178), matching the S125 'A' and S124 'B' markers.
- [F3](../findings.json) (Verification): Reference answers contradict the requested A/B sums and seeded labels
  - Change: All five discrepant reference cells (L134, N132, R132, R134, V132) now equal the sums of the correspondingly tagged inputs.
