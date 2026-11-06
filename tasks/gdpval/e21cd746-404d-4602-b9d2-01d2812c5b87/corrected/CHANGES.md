# Changes: GDPval e21cd746-404d-4602-b9d2-01d2812c5b87

Fix summary (from the fix record):

Guidance task note: the CEO rubric item is read as key customers (what the prompt asks), and a working .pptx beside the PDF does not fail the single-PDF item.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, minor, not in findings.json: Rubric grades a CEO field the prompt never asks for and skips 'key customers', which the prompt explicitly requires
  - Change: graderGuidance: task note sentence telling the grader to read the CEO rubric item as key customers (as the instruction requires) and not to penalise missing CEOs.
- other finding, minor, not in findings.json: Grader guidance penalizes deliverables when the agent saves both the working PowerPoint and the converted PDF as instructed
  - Change: graderGuidance: task note sentence that a working .pptx saved next to the PDF does not fail the single-PDF rubric item.
