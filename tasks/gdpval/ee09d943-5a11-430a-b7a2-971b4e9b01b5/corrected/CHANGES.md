# Changes: GDPval ee09d943-5a11-430a-b7a2-971b4e9b01b5

Fix summary (from the fix record):

The prompt lists AP_TB-1.xlsx but it was never staged, and the public GDPval set omits it too; it cannot be added without inventing it from the expert deliverable, so it is left as a known gap. Full pass: GL 6200 rubric value corrected to the undoubled 435,284.69, seven-organizations item clarified, and the grader told not to credit the expert for checklist items it misses.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: GT Legal 6200 tab double-counts its rows, and the rubric's 870,569.38 is twice the true balance
  - Change: grader_guidance: the [+1] GL 6200 item now expects 435,284.69 (ties to GL 6200 on the April TB and to the expert's own tab 3a) and says the 870,569.38 from Legal_Dump-1.xlsx L62:M63 / expert tab 10 double-counts the row-60 subtotal (L62 =SUM(L3:L61) includes L60 =SUM(L3:L59)).
- other finding, major, not in findings.json: Legal expense totals double-count a subtotal, and the rubric rewards the doubled amount
  - Change: Same GL 6200 rubric change as another finding (not listed) (435,284.69 replaces the doubled 870,569.38).
- other finding, major, not in findings.json: The expert GT fails many of its own rubric checks, which skews the pairwise grade
  - Change: grader_guidance: added one sentence after the scoring line listing the checklist items the expert file itself misses (period text in rows 1-10 on all tabs but #14, TOC lists tabs 1/2/2a/3, no Issues/Notes column, no New marks, no hyperlinks, 'March' on tab 17) and telling the grader not to credit the expert with those items when comparing (same wording pattern as other GDPval fixes).
- other finding, minor, not in findings.json: Funding schedule duplicates a subsidiary while grading expects seven organizations
  - Change: grader_guidance: the [+1] seven-organizations item now says it means the seven subsidiary rows of the March template, where Aurisic UK appears on two rows (A5 and A7), so an agent that carries the duplicated label is not marked down for showing six distinct names.

## Confirmed findings not fixed

- [F2](../findings.json): Source file AP_TB-1.xlsx is listed in the task but never staged, so the A/P Trade schedule cannot be built
  - Reason: cannot-fix-safely: would invent content (the missing AP_TB-1.xlsx could only be rebuilt from the expert deliverable; the public GDPval set does not include it)
- [F1](../findings.json): Required April accounts-payable source is missing
  - Reason: cannot-fix-safely: would invent content (the missing AP_TB-1.xlsx could only be rebuilt from the expert deliverable; the public GDPval set does not include it)
