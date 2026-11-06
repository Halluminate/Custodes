# Changes: GDPval 8079e27d-b6f3-4f75-a9b5-db27903c798d

Fix summary (from the fix record):

The egress proxy blocking open-web sources is infrastructure (critical pass). Full pass: the guidance now accepts a decimal Market Cap in a labelled unit for the integer rubric item; figure accuracy cannot be graded without inventing a reference dataset.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, minor, not in findings.json: The rubric requires market cap as 'non-negative integers', which wrongly fails the common practice of showing it in $bn with decimals
  - Change: graderGuidance: one sentence after the scoring rule: 'The prompt sets no number format for Market Capitalization, so the non-negative integer item is met by non-negative values in a labelled unit even when shown with decimals (e.g., $ billions to one decimal).'
- other finding, major, not in findings.json: Undisclosed constraints in grader rubric (taxonomy declaration, Sources section, non-negative integer Market Cap) not mentioned in problem statement
  - Change: Same guidance sentence as another finding (not listed) for the integer Market Cap item. The taxonomy-declaration and Sources items are left as the author rubric wrote them (reasonable for an open-web sourced deliverable, 5/110 points).
