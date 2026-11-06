# Changes: SpreadsheetBench 2 financial-model-01_03

Fix summary (from the fix record):

The answer key adds an unrequested 2031 date header in 'Working Capital Schedule'!M3, and leaving it blank failed the all-or-nothing check. I removed M3 from answer_position. The historical receivables C4:G4 stay graded, since 'Total Working Capital for all years' needs them.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F2](../findings.json) (Verification): Undisclosed ground-truth modifications on Working Capital Schedule (historical Receivables C4:G4 and terminal header M3) contradict the prompt's explicit scope and non-alteration rule
  - Change: verifications[0].parameters.answer_position: 'Working Capital Schedule'!B2:M24 split so it skips M3 (the unrequested 2031 header =EOMONTH(L3,12)); nothing depends on M3. Locally the golden scores 1.0 and the input with every golden change except M3 also scores 1.0 (before: modification 0.9976, fail). The C4:G4 historical receivables part is not changed: the prompt's 'Total Working Capital for all years' requires them, and they link to 'Consolidated BS' row 15.
- [F3](../findings.json) (Task Spec): An unrequested 2031 date header (Working Capital Schedule!M3) is graded, and leaving it out fails the whole task
  - Change: verifications[0].parameters.answer_position: 'Working Capital Schedule'!B2:M24 split so it skips M3 (the unrequested 2031 header =EOMONTH(L3,12)); nothing depends on M3. Locally the golden scores 1.0 and the input with every golden change except M3 also scores 1.0 (before: modification 0.9976, fail).
- [F1](../findings.json) (Verification): Grader requires an unrequested 2031 date header
  - Change: verifications[0].parameters.answer_position: 'Working Capital Schedule'!B2:M24 split so it skips M3 (the unrequested 2031 header =EOMONTH(L3,12)); nothing depends on M3. Locally the golden scores 1.0 and the input with every golden change except M3 also scores 1.0 (before: modification 0.9976, fail).
- other finding, major, not in findings.json: Ambiguous revenue basis for Maintenance Capex in Fixed Assets Schedule ('% of revenue' vs Operating Revenue vs Total Revenue)
  - Change: Prompt: the Capex sentence now reads "In the Fixed Assets Schedule sheet, calculate Capex for 2026E–2030E, applying the maintenance capex percentage to Total Operating Revenue." (the Revenue Drivers row 135 label the GT uses). Answer key unchanged.
- other finding, major, not in findings.json: Maintenance Capex base is ambiguous: the ground truth uses Operating Revenue, not Total Revenue, and the verifier rejects the Total Revenue reading
  - Change: Same prompt change as another finding (not listed) (maintenance capex applied to Total Operating Revenue).
