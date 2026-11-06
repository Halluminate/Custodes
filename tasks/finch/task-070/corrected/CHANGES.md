# Changes: FINCH task-070

Fix summary (from the fix record):

Guidance task note: the prompt's exact label 'IT Infrastructure Allocation' and the reference's prefixed labels are both accepted, and so is a line under Buildout Amortization or none.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Ground-truth labels drop the 'IT' wording and add per-department prefixes, so they don't match the label the prompt specifies
  - Change: grader guidance: added 'Task note for this problem: the prompt's own label 'IT Infrastructure Allocation' on each new line is as correct as the reference's department-prefixed labels ('CABC Infrastructure Allocation' and so on). The reference adds no line under 'Buildout Amortization (Georganne Hodges)', so accept the output with or without a line there.'
- other finding, major, not in findings.json: Unclear whether 'Buildout Amortization' counts as a support department; the GT leaves it out
  - Change: Same task note: a line under Buildout Amortization is accepted either way.
