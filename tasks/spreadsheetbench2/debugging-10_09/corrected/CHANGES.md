# Changes: SpreadsheetBench 2 debugging-10_09

Fix summary (from the fix record):

The circular revolver loop in the debt schedule never settles under the verifier's forced LibreOffice recalculation, so even the golden workbook failed. The loop cells and their direct dependents are dropped from answer_position, and every reference fix stays graded.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F5](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells is a trivial fail (scores 0.0 on all units and on the golden file itself) due to forced LibreOffice recalculation of an oscillating circular reference
  - Change: verifications[0].parameters.answer_position: the 'Model' and 'P&L Summary' ranges are split into runs that skip 187 cells whose values depend on the iterative revolver/interest loop (Model I:M rows 121-124, 126-127, 141, 146-147, 180-183, 186-190, 193-199 (revolver/interest loop), Model R:T and AL:AN rows 24-25, 27-28, 30-31, Model AW20:AW23, AW37, AW39:AW41, Model X20 and X26 (TEXT multiples of the loop), and 'P&L Summary' G40:K41 and R7:T8). Model!I195 references ending cash I$182, which already contains I195, so LibreOffice's iteration oscillates and the result depends on the starting cache. The cell set is the union of cells that missed the golden's cached values in four starting states (golden recalculated once and twice, re-recalculated, and re-saved without caches). All other ranges are unchanged. grader_guidance.md range note updated. Locally (before: golden failed with modification 0.6471 per the finding), the golden, the golden re-saved without caches, and the golden recalculated once and twice all score regression 1.0, modification 1.0. The 84 remaining regression misses are 4-Wall Analysis line-break text cells, within the 0.2% regression allowance. All 17 fixed formula cells (Model D15, I42:M42, I51, I55, I57, P&L Summary G16, G20, G23, G26, G35, H18, H33, H37) stay graded.
- [F4](../findings.json) (Reward): Golden gate: the ground-truth deliverable does not score full reward
  - Change: Same answer_position change. Locally (before: golden failed with modification 0.6471 per the finding), the golden, the golden re-saved without caches, and the golden recalculated once and twice all score regression 1.0, modification 1.0. The 84 remaining regression misses are 4-Wall Analysis line-break text cells, within the 0.2% regression allowance. All 17 fixed formula cells (Model D15, I42:M42, I51, I55, I57, P&L Summary G16, G20, G23, G26, G35, H18, H33, H37) stay graded.
- [F2](../findings.json) (Reward): Golden solution and verifier fail to converge on non-convergent circular revolver paydown formula under forced LibreOffice recalculation
  - Change: Same answer_position change as verifier-correctness-0.
- [F3](../findings.json) (Reward): The ground truth fails its own verifier: the model's circular debt/interest block recalculates to different values in LibreOffice
  - Change: Same answer_position change as verifier-correctness-0.
- [F1](../findings.json) (Reward): The golden workbook fails its own mandatory recalculation check
  - Change: Same answer_position change as verifier-correctness-0.
