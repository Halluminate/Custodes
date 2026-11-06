# Changes: GDPval 2d06bc0a-89c6-4e89-9417-5ffe725c1bc6

Fix summary (from the fix record):

Full pass: rubric address item accepts the prompt's 'Fraanklyn' spelling.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Grader guidance expects '536-41 Franklyn Ave' whereas problem statement specifies '536-41 Fraanklyn Ave'
  - Change: graderGuidance: address item now also accepts the statement's spelling 'Fraanklyn' (the prompt writes 536-41 Fraanklyn Ave, rubric and expert LOI write Franklyn), so faithful transcription keeps its 2 points.
- other finding, major, not in findings.json: The prompt spells the street 'Fraanklyn', but the rubric and ground truth spell it 'Franklyn'
  - Change: graderGuidance: address item now also accepts the statement's spelling 'Fraanklyn' (the prompt writes 536-41 Fraanklyn Ave, rubric and expert LOI write Franklyn), so faithful transcription keeps its 2 points.
- other finding, major, not in findings.json: Grader uses a different property address from the task
  - Change: graderGuidance: address item now also accepts the statement's spelling 'Fraanklyn' (the prompt writes 536-41 Fraanklyn Ave, rubric and expert LOI write Franklyn), so faithful transcription keeps its 2 points.
