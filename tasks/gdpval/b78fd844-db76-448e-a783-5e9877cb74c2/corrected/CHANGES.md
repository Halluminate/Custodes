# Changes: GDPval b78fd844-db76-448e-a783-5e9877cb74c2

Fix summary (from the fix record):

The prompt's cash date now matches 'It is currently January 2025', the timing rubric item follows it, and the guidance tells the grader which checklist items the expert report itself misses.

Changed files (in this folder):

- prompt.md
- grader_guidance.md

## Fixed

- other finding, minor, not in findings.json: The prompt's dates contradict each other: cash is stated 'as of May 2025' but the current date is January 2025
  - Change: prompt.md: 'As of May 2025, the company has $100 million in available cash' -> 'As of January 2025, ...' (the prompt says 'It is currently January 2025'); graderGuidance timing item -> '[+1] The report acknowledges the timing context (assignment and analysis as of January 2025).' The expert report mentions January 2025 only.
- other finding, minor, not in findings.json: Task and rubric give inconsistent interpretations of the analysis date
  - Change: Same January 2025 prompt and rubric change as another finding (not listed).
- other finding, major, not in findings.json: The ground-truth report fails several of its own rubric items
  - Change: graderGuidance: one sentence before the formatting item says the expert report has no NPV/IRR exhibit and gives Project B's NPV only as success/failure outcomes, so it does not earn those items; the May 2025 item is removed by the another finding (not listed) change.
- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: Same expert-gaps sentence and timing fix as another finding (not listed)/another finding (not listed), so the grader knows which checklist items the expert itself misses. Not re-graded locally (GDPval pairwise AI grader).
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Same as exploit-probe-0.
