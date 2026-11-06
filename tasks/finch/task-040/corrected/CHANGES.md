# Changes: FINCH task-040

Fix summary (from the fix record):

Grader note: names the single L23 error, lets harmless hardcode tidying pass, and says the reference's apostrophe-less sheet names are not expected.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The prompt says "formula errors" (plural) without any scope, but the answer key changes one cell and the binary grader also scores over-editing
  - Change: graderGuidance task note naming the required L23 fix (=SUM(L14:L22)) and accepting value-neutral tidying of the hardcoded-formula cells QA named (L15, N23, pipeline rates) without an over-edit fail. None of those is a real calculation error (L44 also gives the right value), so the key is not extended.
- other finding, minor, not in findings.json: The ground-truth workbook renames original sheets and stretches every sheet to 1,000 rows, so it breaks the task's own rule to preserve all original sheets
  - Change: Same task note: the reference's 'Addtl Info'/'Addtl Info2' names and 1,000-row padding are save leftovers; keeping the original names is correct.
