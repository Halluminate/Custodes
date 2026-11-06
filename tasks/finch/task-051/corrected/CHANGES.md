# Changes: FINCH task-051

Fix summary (from the fix record):

Grader guidance now says a hierarchical type/creditor layout is equivalent to the reference's flat list of the two-ring chart.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The ground truth flattens a two-level creditor hierarchy into one column
  - Change: graderGuidance: one task note added after the opening paragraph: 'Task note: the chart has two rings, creditor types (Private, Multilateral, Bilateral) and the creditors inside each, so an output that keeps this hierarchy, for example a type column and a creditor column, is equivalent to the reference's single list.' Reference file unchanged.
