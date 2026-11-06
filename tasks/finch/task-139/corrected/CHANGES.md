# Changes: FINCH task-139

Fix summary (from the fix record):

Grader-guidance task note: ignore the reference's unrequested scratch cells and Brazos/Cedar Brakes edits, accept Question 1 at 240 MW only or at all capacities, and accept XNPV discounted to either the first payment date or the labelled 12/31 date.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Ground truth contains unrequested calculations in Summary!I110:K117 and unrelated edits in Brazos' i Adjustment and Cedar Brakes, while grader guidance penalizes both omissions against GT and extra modifications beyond instructions
  - Change: graderGuidance: task note (1) tells the judge to ignore the reference's unrequested Summary!I110:K117 scratch cells, Brazos' i Adjustment row 45 edit and Cedar Brakes row shift, and not to count their absence as missing work.
- other finding, major, not in findings.json: Question 1 implied equity value is not computed or compared at 245MW, 258MW, and 263MW in the ground truth
  - Change: graderGuidance: task note (2) accepts Question 1 left at 240 MW (reference) or also filled at 245/258/263 MW.
- other finding, major, not in findings.json: Seeded and reference valuations use a date one month later than their stated measurement dates
  - Change: graderGuidance: task note (3) accepts PVs discounted either to the first payment date (reference, seeded values) or to the labelled 12/31/96 and 12/31/00 dates (about 0.4% lower).
