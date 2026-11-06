# Changes: FINCH task-089

Fix summary (from the fix record):

No change. The only true finding is that the egress proxy blocks sec.gov and the other sources this web-research task needs; that is an environment issue (network allowlist), not a task defect. Full pass: one grader-guidance task note accepting MBX revenue N/A or 0.00 (blank G5 = N/A), either order of the two same-day IPOs, Q3 or Q3 2024, no trailing zeros, and Bloomberg-form tickers.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Undisclosed handling of MBX Biosciences pre-revenue status ('N/A' vs 0) and ground-truth blank cell in Sheet2_Financial_Metrics!G5 contradicting 'fill in with N/A' rule
  - Change: graderGuidance: added one task note listing the equally valid readings the reference does not cover: MBX revenue N/A or 0.00 with consistent dependents, and the blank Sheet2 G5 read as N/A.
- other finding, major, not in findings.json: MBX Biosciences 'N/A' revenue in the answer key rejects a valid 0.00 answer, and the difference spreads into many graded cells
  - Change: graderGuidance: added one task note listing the equally valid readings the reference does not cover: MBX revenue N/A or 0.00 with consistent dependents.
- other finding, major, not in findings.json: Ground-truth format contradiction on 'IPO Quarter' ('Q1 2024' vs 'Q1/Q2/Q3/Q4') and unspecified tie-breaker for identical listing dates in Sheet4_IPO_Timeline
  - Change: graderGuidance: added one task note listing the equally valid readings the reference does not cover: 'Q3' or 'Q3 2024' for IPO Quarter, and either order/numbering for the two 2024/09/13 IPOs.
- other finding, major, not in findings.json: IPO Sequence tie-break is not specified, so one valid order of the two same-day IPOs is penalized (multiple_valid_answers_rejected)
  - Change: graderGuidance: added one task note listing the equally valid readings the reference does not cover: either order of Zenas and MBX (same listing date), numbered 3 and 4 or both 3.
- other finding, major, not in findings.json: The answer key does not follow the format conventions the prompt sets (IPO Quarter, two decimals)
  - Change: graderGuidance: added one task note listing the equally valid readings the reference does not cover: 'Q3' or 'Q3 2024', trailing zeros not required, and the blank G5 read as N/A.
- other finding, minor, not in findings.json: 'Bloomberg ticker' format is ambiguous
  - Change: graderGuidance: added one task note listing the equally valid readings the reference does not cover: exchange ticker or Bloomberg form ('CGON US Equity').
