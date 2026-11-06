# Changes: FINCH task-096

Fix summary (from the fix record):

The prompt's "longer tenor" fits both the template's 5Y anchor (the reference) and the 4Y bond being compared. The guidance now accepts either reading with its own figures.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: AI grader (production): rejects a valid answer on "overall grade"
  - Change: graderGuidance: added one sentence to the opening paragraph: The statement's "longer tenor shifts up by 6bp" can be read as the template's 5Y anchor (B13 = 5, A13 = 5, as in the reference: annualized HPR about 1.6598% for 1Y and 1.5022% for 4Y) or as the 4Y bond being compared (B13 = 4, A13 = 5: about 1.6619% for 1Y and 1.4317% for 4Y), so treat either reading, with its matching yields, prices and returns, as correct and not as an over-edit. Values recomputed from the sheet formulas (5Y anchor reproduces the reference F10 1.79225, F12 1.5022%).
- other finding, major, not in findings.json: Ambiguity and ground-truth mismatch on the longer-tenor yield shift anchor maturity (`B13` = 5Y in GT vs. 4Y in prompt)
  - Change: graderGuidance: added one sentence to the opening paragraph: The statement's "longer tenor shifts up by 6bp" can be read as the template's 5Y anchor (B13 = 5, A13 = 5, as in the reference: annualized HPR about 1.6598% for 1Y and 1.5022% for 4Y) or as the 4Y bond being compared (B13 = 4, A13 = 5: about 1.6619% for 1Y and 1.4317% for 4Y), so treat either reading, with its matching yields, prices and returns, as correct and not as an over-edit. Values recomputed from the sheet formulas (5Y anchor reproduces the reference F10 1.79225, F12 1.5022%).
- other finding, major, not in findings.json: "Longer tenor shifts up by 6bp" is ambiguous, and the answer key anchors the +6bp shift at 5Y, not at the 4Y bond
  - Change: graderGuidance: added one sentence to the opening paragraph: The statement's "longer tenor shifts up by 6bp" can be read as the template's 5Y anchor (B13 = 5, A13 = 5, as in the reference: annualized HPR about 1.6598% for 1Y and 1.5022% for 4Y) or as the 4Y bond being compared (B13 = 4, A13 = 5: about 1.6619% for 1Y and 1.4317% for 4Y), so treat either reading, with its matching yields, prices and returns, as correct and not as an over-edit. Values recomputed from the sheet formulas (5Y anchor reproduces the reference F10 1.79225, F12 1.5022%).
- other finding, major, not in findings.json: Yield-shift scenario leaves the longer-tenor anchor ambiguous
  - Change: graderGuidance: added one sentence to the opening paragraph: The statement's "longer tenor shifts up by 6bp" can be read as the template's 5Y anchor (B13 = 5, A13 = 5, as in the reference: annualized HPR about 1.6598% for 1Y and 1.5022% for 4Y) or as the 4Y bond being compared (B13 = 4, A13 = 5: about 1.6619% for 1Y and 1.4317% for 4Y), so treat either reading, with its matching yields, prices and returns, as correct and not as an over-edit. Values recomputed from the sheet formulas (5Y anchor reproduces the reference F10 1.79225, F12 1.5022%).
