# Changes: FINCH task-128

Fix summary (from the fix record):

Grader-guidance task note stating the reference chart content and that a legend, axis titles and the reference's free-text note are optional.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: graderGuidance: added one task note stating what the reference chart holds (stacked area, title, one band per deal from Volumes B:H over Dec-2001 to Dec-2006, Total excluded) and that a legend, axis titles and the reference's 'continues through May 2013' note are optional.
- other finding, minor, not in findings.json: Reference chart has no legend, so its colored bands can't be told apart
  - Change: graderGuidance: added one task note stating what the reference chart holds (stacked area, title, one band per deal from Volumes B:H over Dec-2001 to Dec-2006, Total excluded) and that a legend, axis titles and the reference's 'continues through May 2013' note are optional.
- other finding, minor, not in findings.json: Reference chart has an unrequested annotation and no axis titles, which the grader could treat as expected or missing content
  - Change: graderGuidance: added one task note stating what the reference chart holds (stacked area, title, one band per deal from Volumes B:H over Dec-2001 to Dec-2006, Total excluded) and that a legend, axis titles and the reference's 'continues through May 2013' note are optional.
- other finding, minor, not in findings.json: Grader guidance is a generic Excel-equivalence rubric with no task-specific checklist
  - Change: graderGuidance: added one task note stating what the reference chart holds (stacked area, title, one band per deal from Volumes B:H over Dec-2001 to Dec-2006, Total excluded) and that a legend, axis titles and the reference's 'continues through May 2013' note are optional.
