# Changes: FINCH task-141

Fix summary (from the fix record):

Corrected the reference's typo for Seung Taek Oh's power book and told the judge that Bryce Schneider's second source power book is acceptable.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_141_ref_0.xlsx

## Fixed

- [F2](../findings.json) (Verification): Ground truth contains a typo ('NETCO-HRLY-ERCOT' instead of 'NETCO-HRLY-ERCT') for Seung Taek Oh's Power Book in Summary!C30
  - Change: gt_141_ref_0.xlsx Summary!C30 'NETCO-HRLY-ERCOT' -> 'NETCO-HRLY-ERCT' (the code in source Master Power!A29). Only that cell changed.
- [F1](../findings.json) (Verification): Answer key gives a power book code for Seung Taek Oh that is not in the source workbook
  - Change: Same GT fix: Summary!C30 now 'NETCO-HRLY-ERCT'.
- [F3](../findings.json) (Verification): Reference workbook disagrees with the source trader-to-book mappings
  - Change: GT Summary!C30 typo fixed as above, and one sentence added to grader guidance after the opening paragraph: 'Bryce Schneider has two power books in Master Power (NETCO-ST-NY and NETCO-HRLY-NY), so Summary!C13 may hold NETCO-ST-NY alone or both books.'
