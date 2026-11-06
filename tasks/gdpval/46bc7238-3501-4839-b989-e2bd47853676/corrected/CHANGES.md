# Changes: GDPval 46bc7238-3501-4839-b989-e2bd47853676

Fix summary (from the fix record):

Full pass: graderGuidance now notes that the expert deliverable has no actual one-page flyer or contact details.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Ground-truth PDF omits the required one-page flyer template example and fails 12 of 67 points in its own rubric
  - Change: graderGuidance: added one sentence to the opening paragraph: "The expert's page 5 lists what the flyer must contain but is not itself a one-page flyer and gives no contact details, so the expert earns none of the flyer items, and an agent's actual one-page flyer with overview, highlights and contact information is work the expert did not do." No rubric line or prompt change.
- other finding, major, not in findings.json: Ground-truth playbook fails many of its own rubric items, so it is a poor reference for grading
  - Change: graderGuidance: added one sentence to the opening paragraph: "The expert's page 5 lists what the flyer must contain but is not itself a one-page flyer and gives no contact details, so the expert earns none of the flyer items, and an agent's actual one-page flyer with overview, highlights and contact information is work the expert did not do." No rubric line or prompt change.
