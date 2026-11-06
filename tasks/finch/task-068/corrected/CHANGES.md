# Changes: FINCH task-068

Fix summary (from the fix record):

Grader guidance note: accept any of the three summary index prices for the six volumetric operators whose sheets link to none, and accept 'Volumetric' for Williams.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The answer key uses a different price index for some volumetric operators, and nothing in the workbook tells the agent which one
  - Change: graderGuidance: task note after the opening paragraph accepting Dollars from any of summary G3:G5 for Northwest, Amoco Florida, NGPL, SoCal, PG&E Topock and Panhandle Eastern (their sheets reference no index; the reference mixes SJ 2.09, AVG 2.08 and NTXPH 2.08), totals following. Williams keeps the key's SJ index because its sheet has a San Juan index column. Official judge text kept verbatim. Not regraded locally (AI judge).
- other finding, major, not in findings.json: The answer key's 'Imbal Type' label contradicts its own formula for Williams
  - Change: Same task note: Williams row 48 Imbal Type may be 'Volumetric' or the reference's 'Dollar Valued'.
