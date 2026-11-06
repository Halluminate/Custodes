# Changes: GDPval feb5eefc-39f1-4451-9ef9-bffe011b71dd

Fix summary (from the fix record):

Full pass: rubric's cash AGI limit corrected to the 2015 50% figure, inapplicable 'If …' items left out of the total, and substance-over-wording credit stated.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, minor, not in findings.json: Grader rubric requires post-2017 (60% of AGI) cash charitable deduction limit despite 2015 problem timeframe
  - Change: graderGuidance: AGI item now reads 'cash contributions are limited to 50% of AGI under 2015 law (60% applies only to tax years after 2017)'; the 30% capital-gain part is unchanged.
- other finding, minor, not in findings.json: Rubric's AGI-limit item uses the post-2017 60% cash limit, which contradicts the task's stated 2015 setting
  - Change: Same AGI item change as another finding (not listed).
- other finding, minor, not in findings.json: CRAT deduction rubric uses a post-2015 cash contribution limit
  - Change: Same AGI item change as another finding (not listed).
- other finding, minor, not in findings.json: Conditional 'If…' rubric items count in the denominator, so agents that correctly skip them lose points
  - Change: graderGuidance: added after the scoring sentence: an 'If …' item whose condition does not apply is left out of the total.
- other finding, minor, not in findings.json: AI grader (production): rejects a valid answer on "overall grade"
  - Change: graderGuidance: AGI item fixed to the 2015 50% limit, and added one sentence crediting an item when its substance is conveyed in different words.
