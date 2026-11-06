# Changes: GDPval fd3ad420-6f7d-43b1-a990-c0c5c047d071

Fix summary (from the fix record):

The rubric scored the literal firm name 'EstateWell Realty', which only the expert PDF uses, while the prompt and Word file say 'Sample Realty'. The three rubric items now name Sample Realty, and one guidance sentence tells the judge the two names are the same firm. Full pass: the split-structure heading item accepts a heading that begins with the phrase, and the seed docx opens in LibreOffice (package XML namespace re-serialized).

Changed files (in this folder):

- grader_guidance.md
- inputs/Compensation Model Ideas.docx

## Fixed

- [F3](../findings.json) (Reward): Grader guidance and ground truth require the undisclosed firm name 'EstateWell Realty' instead of 'Sample Realty'
  - Change: grader_guidance.md: in the [+1] firm-name item, the [+2] Purpose-section item and the [+1] onboarding-bonus item, 'EstateWell Realty' -> 'Sample Realty'. Added after the scoring line: 'The expert deliverable calls the firm EstateWell Realty, which is the same firm the task calls Sample Realty, so accept either name and do not mark the agent down for using Sample Realty.'
- [F1](../findings.json) (Reward): Rubric requires the firm name 'EstateWell Realty', which no agent-visible source contains. The prompt and the seed file name the firm 'Sample Realty'
  - Change: grader_guidance.md: in the [+1] firm-name item, the [+2] Purpose-section item and the [+1] onboarding-bonus item, 'EstateWell Realty' -> 'Sample Realty'. Added after the scoring line: 'The expert deliverable calls the firm EstateWell Realty, which is the same firm the task calls Sample Realty, so accept either name and do not mark the agent down for using Sample Realty.'
- [F2](../findings.json) (Verification): Grader requires a different firm name from the task and reference document
  - Change: grader_guidance.md: in the [+1] firm-name item, the [+2] Purpose-section item and the [+1] onboarding-bonus item, 'EstateWell Realty' -> 'Sample Realty'. Added after the scoring line: 'The expert deliverable calls the firm EstateWell Realty, which is the same firm the task calls Sample Realty, so accept either name and do not mark the agent down for using Sample Realty.'
- other finding, minor, not in findings.json: The GT's split heading does not meet the rubric's exact-heading check
  - Change: grader_guidance.md: the Commission Split Structure heading item now reads 'equals or begins with', so the expert's 'Commission Split Structure (Default) For All Transactions:' and similar headings qualify.
- other finding, minor, not in findings.json: Supplied Word reference cannot be opened by the installed LibreOffice
  - Change: Compensation Model Ideas.docx: [Content_Types].xml and _rels/.rels re-serialized with the default namespace instead of the ns0: prefix (same elements and attributes, no content change). LibreOffice 'source file could not be loaded' before, converts cleanly after (checked with soffice --convert-to pdf).
