# Changes: FINCH task-091

Fix summary (from the fix record):

The brief reference answer now also lists the intermediate figures the prompt asks for (mids, spreads, per-leg P&L), in gt_answer.txt and in the guidance reference block.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_answer.txt

## Fixed

- other finding, major, not in findings.json: Reference answer in grader guidance omits most required calculations and input quotes are unavailable to the fresh-container grader
  - Change: gt_answer.txt and the 'Reference answer (text)' block in the grader guidance: one sentence appended with the workings computed from 91_src_0.xlsx row 22 (mids 47.625/55.20 -> 49.125/54.125, spreads 7.575 -> 5.00, 1,488 baseload hours at 100 MW, Cinergy leg +$223,200, PJM-W leg +$159,960, total $383,160). The existing text is unchanged.
- other finding, major, not in findings.json: Grader guidance Criterion 2 requires every model-generated value to have corresponding data in the incomplete reference answer
  - Change: Same reference sentence: every requested figure now has a counterpart in the reference.
- other finding, major, not in findings.json: The grader guidance gives only the final total, not the intermediate figures it asks for
  - Change: Same reference sentence with the intermediate figures.
