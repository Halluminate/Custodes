# Changes: FINCH task-145

Fix summary (from the fix record):

Full pass: one grader-guidance note so a correctly sourced BLS/FRED vintage is accepted and the derived sheets are judged on the model's own RawData.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The reference data comes from a mix of older data releases, the prompt names no source or release, and the binary grader only allows tolerance if it decides this is a web-search task
  - Change: grader_guidance.md: added one note after the web-search tolerance note: treat this as a web-search task, accept RawData values matching any official BLS/FRED not-seasonally-adjusted release for that state and month, and judge Sheet2-Sheet5 by correct computation from the model's own RawData rather than closeness to the reference (same pattern as the HPI FINCH task 66205067).
