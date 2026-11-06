# Changes: FINCH task-100

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Ground truth workbook gt_100_ref_0.xlsx has an empty Sheet2, contradicting the prompt requirement to preserve all original sheets and their contents
  - Change: graderGuidance: added task note (1) telling the judge the reference Sheet2 is blank but the input Sheet2 roster must be kept (keeping it is correct, clearing it is an over-edit).
- other finding, major, not in findings.json: The ground truth empties Sheet2, which breaks the instruction to keep all original sheets and their contents
  - Change: Same graderGuidance task note (1).
- other finding, minor, not in findings.json: The source data in Sheet2 contains misspelled names, and the GT copies them, so an agent that keeps the correct Sheet1 spelling may be marked wrong
  - Change: graderGuidance: added task note (2) accepting either the Sheet1 or Sheet2 spelling of Bardal/Bardel, Renneberg/Rennebeerg, Rothrock/Rothtock.
- other finding, major, not in findings.json: The GT counts the 'Donlevy-Lee/Panchuk' entry as 1 person, which may understate headcount and the % Total figures
  - Change: graderGuidance: added task note (3) accepting the Donlevy-Lee/Panchuk entry counted as one or two people when the counts, totals and % Totals follow consistently.
- other finding, major, not in findings.json: Reference headcount counts two named employees as one
  - Change: Same graderGuidance task note (3).
