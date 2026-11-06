# Changes: FINCH task-137

Fix summary (from the fix record):

The judge compared NC_PL formatting pass/fail to one reference whose bold choices themselves depart from NC_BS. The guidance now judges NC_PL against NC_BS's conventions and tolerates row-level bold/border choices that differ from the reference.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The ground truth's NC_PL formatting does not follow NC_BS's own style rules, yet it is the pass/fail reference
  - Change: graderGuidance: added two sentences after the opening paragraph telling the judge to check NC_PL against NC_BS's visible conventions (fonts and sizes, number format, year-header layout, total-row borders, section-header emphasis) and not to fail an output only because its row-level bold/border choices differ from the reference, provided NC_BS's conventions are applied consistently. The GT (which bolds totals instead of ':' headers) and a faithful NC_BS-style output both pass under it. Not re-run with the LLM grader.
- other finding, major, not in findings.json: One-line formatting instruction is graded pass/fail against a single reference styling, so other valid stylings get rejected
  - Change: Same graderGuidance change.
- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: Same graderGuidance change: the GT's off-convention row emphasis is no longer a reason to fail it. Residual LLM-judge variance is grader behaviour.
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Same graderGuidance change.
