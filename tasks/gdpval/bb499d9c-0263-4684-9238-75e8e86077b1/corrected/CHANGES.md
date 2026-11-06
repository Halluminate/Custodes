# Changes: GDPval bb499d9c-0263-4684-9238-75e8e86077b1

Fix summary (from the fix record):

Grader guidance now judges the page-length rubric item against the prompt's 25-page limit and credits the requested Key Forms section and flow-chart diagrams that the expert deliverable and rubric leave out.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Grader guidance enforces a 15-page limit that contradicts the 25-page limit stated in problem.py
  - Change: graderGuidance: added one sentence after "negative items subtract their points.": "The statement allows the document to run to 25 pages, so judge the page-length item against 25 pages: a .docx of 16 to 25 pages meets it as fully as one of 15 pages or fewer."
- other finding, major, not in findings.json: Section 5 ('Key Forms') required by problem.py is missing from both grader_guidance and the ground-truth document
  - Change: graderGuidance: added one sentence after the page-length sentence: "The statement also asks for a Key Forms section (section 5) and a visual flow-chart diagram for each of the issuer and retail investor process models (sections 9 and 10), which neither the expert deliverable nor the rubric covers, so credit an agent that includes them and count their absence against the agent's work, not in its favour."
- other finding, major, not in findings.json: Visual flow chart diagrams required in Sections 9 and 10 are neither checked by grader_guidance nor present in the ground-truth document
  - Change: graderGuidance: added one sentence after the page-length sentence: "The statement also asks for a Key Forms section (section 5) and a visual flow-chart diagram for each of the issuer and retail investor process models (sections 9 and 10), which neither the expert deliverable nor the rubric covers, so credit an agent that includes them and count their absence against the agent's work, not in its favour."
- other finding, major, not in findings.json: The grader guidance sets a 15-page limit, but the prompt allows up to 25 pages
  - Change: graderGuidance: added one sentence after "negative items subtract their points.": "The statement allows the document to run to 25 pages, so judge the page-length item against 25 pages: a .docx of 16 to 25 pages meets it as fully as one of 15 pages or fewer."
- other finding, major, not in findings.json: The ground-truth document leaves out several required sections, including both flow-chart diagrams and the issuer-group variations
  - Change: graderGuidance: added one sentence after the page-length sentence: "The statement also asks for a Key Forms section (section 5) and a visual flow-chart diagram for each of the issuer and retail investor process models (sections 9 and 10), which neither the expert deliverable nor the rubric covers, so credit an agent that includes them and count their absence against the agent's work, not in its favour."
- other finding, major, not in findings.json: Grader applies an undisclosed 15-page limit
  - Change: graderGuidance: added one sentence after "negative items subtract their points.": "The statement allows the document to run to 25 pages, so judge the page-length item against 25 pages: a .docx of 16 to 25 pages meets it as fully as one of 15 pages or fewer."
