# Changes: FINCH task-162

Fix summary (from the fix record):

The input is only the balance sheet, but the reference explains growth with facts from the adidas Annual Report text, and the 0/1 judge demanded equivalence. One guidance sentence now tells the judge those Annual Report reasons are not required and to accept reasons consistent with the figures.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- [F1](../findings.json) (Verification): Ground truth reference document requires external qualitative commentary and currency-neutral metrics absent from the provided Excel file while prompt restricts task to 'Based on the provided financial data'
  - Change: graderGuidance: appended one sentence to the opening paragraph: 'The only input is the adidas balance sheet in 162_src_0.xlsx, so the growth reasons in the reference that come from the adidas Annual Report text (Reebok earn-out and customs refund reclassifications, the new distribution center, currency-neutral growth rates, currency effects on goodwill) are not required; accept any reasons that are consistent with the balance-sheet figures and fail only reasons that contradict them.'
- [F3](../findings.json) (Environment & Infra): The reference answer's growth reasons cannot be derived from the only input file, and grading is pass/fail against that reference
  - Change: Same guidance sentence as F1.
- [F2](../findings.json) (Environment & Infra): Supporting disclosures for the required growth explanations are not supplied
  - Change: Same guidance sentence as F1: reasons that need the unstaged Notes/Annual Report are no longer required.
