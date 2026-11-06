# Changes: GDPval 7d7fc9a7-21a7-4b83-906f-416dea5ad04f

Fix summary (from the fix record):

Guidance now says the invoices carry no service or policy dates and lists the expert workbook's own slips so the pairwise grader does not penalize an agent for differing on them.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Grader guidance requires start/end date columns and PDF policy dates that do not exist in the source PDFs or ground-truth workbook
  - Change: graderGuidance: appended to the opening paragraph 'The invoice PDFs show only invoice dates, so judge amortization periods against the policy periods given in the statement and the six-month default, not against dates on the invoices.' Also: graderGuidance: appended to the opening paragraph a sentence listing the expert workbook's slips (Amortization Months instead of start/end dates, no per-month GL variance on 1250, Global Services sorted before Expertek, UHY advising coded to 6600 Advertising) and telling the grader not to mark the agent down for differing on them.
- other finding, minor, not in findings.json: Rubric says amortization periods and policy dates are 'shown on' the invoice PDFs, but no invoice shows any dates
  - Change: graderGuidance: appended to the opening paragraph 'The invoice PDFs show only invoice dates, so judge amortization periods against the policy periods given in the statement and the six-month default, not against dates on the invoices.'
- other finding, major, not in findings.json: Ground-truth workbook has missing monthly variance checks on 1250, misclassified COA account for UHY ('Advising' mapped to 6600 'Advertising'), and unsorted rows
  - Change: graderGuidance: appended to the opening paragraph a sentence listing the expert workbook's slips (Amortization Months instead of start/end dates, no per-month GL variance on 1250, Global Services sorted before Expertek, UHY advising coded to 6600 Advertising) and telling the grader not to mark the agent down for differing on them.
- other finding, minor, not in findings.json: Ground truth maps UHY 'Advising' invoices to COA 6600 'Advertising'
  - Change: graderGuidance: appended to the opening paragraph a sentence listing the expert workbook's slips (Amortization Months instead of start/end dates, no per-month GL variance on 1250, Global Services sorted before Expertek, UHY advising coded to 6600 Advertising) and telling the grader not to mark the agent down for differing on them.
- other finding, minor, not in findings.json: GT lacks the per-month GL Balance/Variance check the rubric requires, and its 1250 'G.L. Balance' row is the computed balance pasted in, not the GL figures given
  - Change: graderGuidance: appended to the opening paragraph a sentence listing the expert workbook's slips (Amortization Months instead of start/end dates, no per-month GL variance on 1250, Global Services sorted before Expertek, UHY advising coded to 6600 Advertising) and telling the grader not to mark the agent down for differing on them.
- other finding, minor, not in findings.json: GT 1250 schedule is not fully sorted by vendor, although the prompt requires 'sorted by vendor'
  - Change: graderGuidance: appended to the opening paragraph a sentence listing the expert workbook's slips (Amortization Months instead of start/end dates, no per-month GL variance on 1250, Global Services sorted before Expertek, UHY advising coded to 6600 Advertising) and telling the grader not to mark the agent down for differing on them.
