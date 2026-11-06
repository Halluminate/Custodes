# Changes: FINCH task-101

Fix summary (from the fix record):

Full pass: grader guidance now states the one expected change (B4:FT4 to uppercase 01-MMM-YYYY text) so the judge grades the key consistently.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: graderGuidance: added a task-specific note stating the reference change (Sheet1!B4:FT4 become uppercase '01-JUN-2001' ... '01-DEC-2015', nothing else changes) and the pass condition. Official judge text kept verbatim.
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Same graderGuidance note as exploit-probe-0.
