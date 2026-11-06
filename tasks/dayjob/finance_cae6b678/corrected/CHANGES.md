# Changes: DAYJOB finance_cae6b678

Fix summary (from the fix record):

Full pass: c054 accepts the FY2025E or FY2026E apparent cushion and the c024 NI range; c036 applies only when the response raises the timing argument.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, minor, not in findings.json: c054 cushion arithmetic mixes fiscal years and uses an NI range that conflicts with c024
  - Change: graderGuidance c054: the apparent cushion may be computed on FY2025E (80% x $4.48M - $2.3M = ~$1.3M, matching the cash-flow statement's $3.58M FY2025E distributions) or FY2026E (~$2.2M), and the corrected net-income range is $1.7M-$3.2M to match c024, so a year-matched reconciliation is no longer rejected.
- other finding, minor, not in findings.json: Distribution-cushion grading criterion mixes forecast years
  - Change: graderGuidance c054: the apparent cushion may be computed on FY2025E (80% x $4.48M - $2.3M = ~$1.3M, matching the cash-flow statement's $3.58M FY2025E distributions) or FY2026E (~$2.2M), and the corrected net-income range is $1.7M-$3.2M to match c024, so a year-matched reconciliation is no longer rejected.
- other finding, major, not in findings.json: Rubric requires rebutting arguments that no source material ever makes (multiple_valid_answers_rejected / output_scope_mismatch)
  - Change: graderGuidance c036 made conditional: it applies only when the response raises the 'draw once 2025E EBITDA materializes' timing argument, which no source makes (c057 still requires rejecting the $8.12M/$9.74M covenant base). c054 kept mandatory: the uncorrected cushion is implicit in the FP&A cash-flow statement's forecast distributions.
