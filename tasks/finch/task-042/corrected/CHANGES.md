# Changes: FINCH task-042

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The prompt gives the discount rate as 9.13%, but the workbook and answer key use 9.12547%, so the answer key's $40M savings figure moves
  - Change: graderGuidance: added a task note after the opening paragraph accepting NPVs discounted at exactly 9.13% (Old PPA about 534,200,162, PPA Savings about 39,989,376) as well as the reference's G6 rate 0.0912547. Official judge text kept verbatim. Not regraded locally (AI judge).
