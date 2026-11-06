# Changes: SpreadsheetBench 2 debugging-03_01

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: The prompt asks for a thorough audit that includes naming and labelling fixes, but the grader scores 0 when an agent makes those fixes
  - Change: verifications answer_position (+ graderGuidance): left out the named open-ended cleanup cells that have no single exact answer: label text LBO!H23, H24, H31, J31:N31, H69, 'Ex 10 - Forecast Assumptions '!B35, 'Ex 3 - Balance Sheet'!B10, and the hardcoded exit cash LBO!Q15:V15 with its dependents Q16:V16 and R19:V20 (constant vs per-year minimum cash). Planted double-count cells stay graded. Real scorer: golden 1.0; golden + these cleanups 1.0 (was reg 0.9959, mod 0.72); untouched input fails (mod 0.0).
