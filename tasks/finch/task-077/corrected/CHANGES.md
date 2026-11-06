# Changes: FINCH task-077

Fix summary (from the fix record):

Grader-guidance note: accepts both readings of 'Donlevy-Lee/Panchuk' (32/87 or 33/88), and makes the reference's extra subtotal rows and columns optional.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The answer key counts 'Donlevy-Lee/Panchuk' as one person, but it can just as fairly be read as two
  - Change: Added a grader-guidance task note that accepts both 32/87 (36.8/37.9/25.3%) and 33/88 (37.5/37.5/25.0%).
- other finding, major, not in findings.json: Ambiguous roster entry leaves the headcount convention unspecified
  - Change: Same grader-guidance note: both counts accepted.
- other finding, minor, not in findings.json: The prompt asks only for group totals, but the answer key also adds a per-department count row and inserts rows
  - Change: Same grader-guidance note: says the per-department rows, extra columns and inserted row are optional, and that a reference-style layout is not an over-edit.
