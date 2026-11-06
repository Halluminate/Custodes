# Changes: FINCH task-049

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Prompt misdescribes the defect: the only error is a transposed digit, not missing cell references
  - Change: graderGuidance: added a task note after the opening paragraph naming G10 (178232 -> 172832, G10 -64,252, G16 8,898) as the only mismatch and accepting either the corrected constant or formulas in A1:K16 rewritten to cell references with matching values, not counted as over-edits. Official judge text kept verbatim. Not regraded locally (AI judge).
