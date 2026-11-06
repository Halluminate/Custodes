# Changes: FINCH task-123

Fix summary (from the fix record):

Grader-guidance note: the dollar-neutral answer given as a percentage return (about −7.2%) is accepted as equivalent to the −2.0 dollars per unit reference.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: 'Nominal return' is given in dollars, so a correct percentage answer may be marked wrong
  - Change: graderGuidance: added after the reference answer a task note accepting the dollar-neutral return stated as a percentage (about −7.2% of the power-leg notional) as equivalent to −2.0 dollars per unit.
- other finding, major, not in findings.json: Underspecified portfolio scaling and 'nominal return' definition cause valid interpretations to differ from the single reference value (-2.0 dollars)
  - Change: Same task note as another finding (not listed) (the 'nominal return' unit part of this finding); the sizing part is not a defect (see label).
