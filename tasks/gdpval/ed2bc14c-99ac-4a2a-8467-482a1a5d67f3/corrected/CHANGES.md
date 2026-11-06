# Changes: GDPval ed2bc14c-99ac-4a2a-8467-482a1a5d67f3

Fix summary (from the fix record):

The guidance now tells the pairwise grader which checklist items the expert memo itself misses.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The ground-truth memo fails several rubric items the grader uses for pairwise comparison
  - Change: graderGuidance: one sentence before the formatting item lists the checklist items the expert memo misses (Stamford, 90-day deadline, quantified 60-day rate and month-to-month premium, 9/20 and 5/20 counts, coffee-event cost control, email deadlines/call to action), checked against gt_Tenant Rentention Strategy.docx.
- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: Same expert-gaps sentence as another finding (not listed), so the pairwise grader has a stable view of where the expert falls short. Not re-graded locally (GDPval pairwise AI grader).
