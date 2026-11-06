# Changes: FINCH task-159

Fix summary (from the fix record):

The prompt asked the agent to fill 'previously missing columns' on Benchmark Returns, but that sheet is complete in the input and unchanged in the reference, so agents over-edited and graders split on completeness. One prompt sentence now says the sheet is complete and should be left unchanged.

Changed files (in this folder):

- prompt.md

## Fixed

- [F1](../findings.json) (Task Spec): Prompt instructs agent to fill missing columns and add summary formulas on 'Benchmark Returns' sheet, but 'Benchmark Return' is already complete in source and unchanged in ground truth
  - Change: prompt.md: replaced the sentence 'On Benchmark Returns, fill in the previously missing columns using the same logic as the existing columns, validate ... tracking view.' with 'The Benchmark Returns sheet is already complete and should be left unchanged, so validate that its annual breakdown is behaving normally and add formulas to summarize performance across the full sample period with results flowing back to the tracking view.' The source 'Benchmark Return' sheet is fully populated and identical in the GT, whose only changes are the orange Timing_Strategy cells X23:AH23 and AE27:AE39.
- [F2](../findings.json) (Task Spec): Prompt asks for 'previously missing columns' on Benchmark Returns to be filled, but nothing is missing there and the GT leaves that sheet unchanged
  - Change: Same prompt sentence change.
- [F3](../findings.json) (Environment & Infra): The requested missing Benchmark Return columns are already populated
  - Change: Same prompt sentence change.
- other finding, critical, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: Same prompt sentence change: the grade swing on the GT came from the completeness requirement on the nonexistent missing columns, which the prompt no longer asks for.
- other finding, critical, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Same prompt sentence change: the GT's low guidance-test grade came from the same unmet 'fill missing columns' instruction.
