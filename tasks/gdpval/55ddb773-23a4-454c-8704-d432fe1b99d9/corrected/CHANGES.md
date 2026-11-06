# Changes: GDPval 55ddb773-23a4-454c-8704-d432fe1b99d9

Fix summary (from the fix record):

graderGuidance: keyword-label items may split words between a heading and the question beneath it; the Architectural blank-lines label is optional; the PDF need not be multi-page.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Grader guidance enforces undisclosed substring requirements on prompt labels that conflict with the source PDF's hierarchy and wording
  - Change: graderGuidance: one sentence added after the scoring paragraph: where an item says the label contains certain words, the words may be split between a heading and the question listed under it, as in the attached PDF (example 'Fencing' above 'Does one damaged post warrant violation?'). Also the Architectural blank-lines item's '(label contains "Additional" and either "Architectural" or "Community")' now reads '(a label is optional)'.
- other finding, major, not in findings.json: Rubric requires literal keywords in each label, which can penalize forms that follow the source's own heading-and-question layout
  - Change: graderGuidance: one sentence added after the scoring paragraph: where an item says the label contains certain words, the words may be split between a heading and the question listed under it, as in the attached PDF (example 'Fencing' above 'Does one damaged post warrant violation?').
- other finding, minor, not in findings.json: Rubric requires a label wording for the blank architectural lines that the prompt never asks for
  - Change: graderGuidance: in the item 'After the Architectural Regulations items, the form provides at least three blank lines...', '(label contains "Additional" and either "Architectural" or "Community")' -> '(a label is optional)'.
- other finding, minor, not in findings.json: Grader guidance requires a multi-page PDF deliverable when the prompt does not specify page count
  - Change: graderGuidance: '[+2] Exactly one PDF file (single multi-page document)' -> '(single document)'.
