# Changes: FINCH task-132

Fix summary (from the fix record):

Grader-guidance note scopes grading to the two requested changes and neutralizes the reference's unrequested edits. In the answer key, the misplaced TOTAL EWS YTD formula moved from AF87 to AF7. Full pass: the guidance also accepts any reasonable EWS unit/column scope for TOTAL EWS.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_132_ref_0.xlsx

## Fixed

- other finding, critical, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: Added a grader-guidance note that limits the graded work to the reclass of the ENA P&L lines and the TOTAL EWS row. It lists the reference's unrequested edits (A9 label, /1000 rescaling, 610/0/0 in Weather Derivatives, rebuilt Cross Commodity rows) as neither required nor penalized, and says to check TOTAL EWS against the output's own unit rows. Answer key: the TOTAL EWS YTD formula =+AF72+AF63+AF55+AF32+AF9 moved from the orphan cell AF87 to AF7 (its row). No other cell changed.
- other finding, critical, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Added a grader-guidance note that limits the graded work to the reclass of the ENA P&L lines and the TOTAL EWS row. It lists the reference's unrequested edits (A9 label, /1000 rescaling, 610/0/0 in Weather Derivatives, rebuilt Cross Commodity rows) as neither required nor penalized, and says to check TOTAL EWS against the output's own unit rows. Answer key: the TOTAL EWS YTD formula =+AF72+AF63+AF55+AF32+AF9 moved from the orphan cell AF87 to AF7 (its row). No other cell changed.
- [F1](../findings.json) (Verification): Ground truth contains undisclosed edits and an unobtainable hardcoded value in ENRON GLOBAL MARKETS and ENRON INDUSTRIAL MARKETS that cascade into TOTAL EWS
  - Change: Added a grader-guidance note that limits the graded work to the reclass of the ENA P&L lines and the TOTAL EWS row. It lists the reference's unrequested edits (A9 label, /1000 rescaling, 610/0/0 in Weather Derivatives, rebuilt Cross Commodity rows) as neither required nor penalized, and says to check TOTAL EWS against the output's own unit rows.
- [F2](../findings.json) (Verification): Answer key makes many edits the instruction never asks for: labels changed, units rescaled, placeholders filled, rows restructured
  - Change: Added a grader-guidance note that limits the graded work to the reclass of the ENA P&L lines and the TOTAL EWS row. It lists the reference's unrequested edits (A9 label, /1000 rescaling, 610/0/0 in Weather Derivatives, rebuilt Cross Commodity rows) as neither required nor penalized, and says to check TOTAL EWS against the output's own unit rows.
- other finding, major, not in findings.json: Task statement and ground truth leave 'TOTAL EWS' scope/columns and 'ENRON AMERICA' row restructuring ambiguous and over-specified
  - Change: graderGuidance task note: after 'sums the business-unit header rows.' added 'The instruction does not say which units or columns make up EWS, so accept any reasonable set the output uses (for example with or without EWS Office of the Chair or Enron Global Assets, and with or without the E/G and P/Q columns), provided the row correctly sums the output's own unit rows.' (ENA restructuring part was already covered by the critical-pass note.)
- other finding, major, not in findings.json: 'TOTAL EWS' line is underspecified: no definition of which divisions or columns it covers
  - Change: graderGuidance task note: after 'sums the business-unit header rows.' added 'The instruction does not say which units or columns make up EWS, so accept any reasonable set the output uses (for example with or without EWS Office of the Chair or Enron Global Assets, and with or without the E/G and P/Q columns), provided the row correctly sums the output's own unit rows.'
- other finding, major, not in findings.json: The requested TOTAL EWS aggregation is not defined in the task inputs
  - Change: graderGuidance task note: after 'sums the business-unit header rows.' added 'The instruction does not say which units or columns make up EWS, so accept any reasonable set the output uses (for example with or without EWS Office of the Chair or Enron Global Assets, and with or without the E/G and P/Q columns), provided the row correctly sums the output's own unit rows.'
