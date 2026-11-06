# Changes: FINCH task-165

Fix summary (from the fix record):

 Full pass: grader guidance lists the nine rows and accepts any red fill.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: graderGuidance: added task note listing the nine expected rows and accepting any red fill on exactly the values above 600,000 (the reference's light-red preset and dead second rule are not required).
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: graderGuidance: added task note listing the nine expected rows and accepting any red fill on exactly the values above 600,000 (the reference's light-red preset and dead second rule are not required).
- other finding, minor, not in findings.json: The ground-truth conditional formatting uses a light-red preset and also contains a broken extra rule
  - Change: graderGuidance: added task note listing the nine expected rows and accepting any red fill on exactly the values above 600,000 (the reference's light-red preset and dead second rule are not required).
