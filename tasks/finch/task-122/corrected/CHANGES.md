# Changes: FINCH task-122

Fix summary (from the fix record):

Corrected the reference's General Support Services pie so it covers only the 9 General Support Services items and their share of the 57.39M General Support total, not 13 rows that included four other functions.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_122_ref_0.xlsx

## Fixed

- other finding, critical, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Reference gt_122_ref_0.xlsx: the bottom General Support Services pie (chart6.xml) now plots only the 9 General Support Services items, '4'!C15:C23 / D15:D23 (Board Office through Operation of Plant, total 57,389,846.70). The four other functions (Maintenance of Plant, Community Services, Debt Services, Other Misc) are gone, with their cached points, dPt and dLbl entries removed. The helper percentages '4'!K15:K23 now divide by SUM($D$15:$D$23) instead of D29 (e.g. Operation of Plant 32%, School Adm 24%), K24:K27 are cleared, and calcChain is updated to match. Direct XML edit, no other cell or chart changed. The LibreOffice render shows the 9-slice pie.
- [F3](../findings.json) (Task Spec): Ambiguity and ground-truth contradiction regarding source table, columns, and row scope for the bottom pie chart ('breakdown of General Support Services')
  - Change: Reference gt_122_ref_0.xlsx: the bottom General Support Services pie (chart6.xml) now plots only the 9 General Support Services items, '4'!C15:C23 / D15:D23 (Board Office through Operation of Plant, total 57,389,846.70). The four other functions (Maintenance of Plant, Community Services, Debt Services, Other Misc) are gone, with their cached points, dPt and dLbl entries removed. The helper percentages '4'!K15:K23 now divide by SUM($D$15:$D$23) instead of D29 (e.g. Operation of Plant 32%, School Adm 24%), K24:K27 are cleared, and calcChain is updated to match. Direct XML edit, no other cell or chart changed. The LibreOffice render shows the 9-slice pie.
- [F2](../findings.json) (Verification): The answer key's General Support Services pie includes four rows from other functions
  - Change: Reference gt_122_ref_0.xlsx: the bottom General Support Services pie (chart6.xml) now plots only the 9 General Support Services items, '4'!C15:C23 / D15:D23 (Board Office through Operation of Plant, total 57,389,846.70). The four other functions (Maintenance of Plant, Community Services, Debt Services, Other Misc) are gone, with their cached points, dPt and dLbl entries removed. The helper percentages '4'!K15:K23 now divide by SUM($D$15:$D$23) instead of D29 (e.g. Operation of Plant 32%, School Adm 24%), K24:K27 are cleared, and calcChain is updated to match. Direct XML edit, no other cell or chart changed. The LibreOffice render shows the 9-slice pie.
- [F1](../findings.json) (Verification): Reference General Support chart includes four unrelated expenditure functions
  - Change: Reference gt_122_ref_0.xlsx: the bottom General Support Services pie (chart6.xml) now plots only the 9 General Support Services items, '4'!C15:C23 / D15:D23 (Board Office through Operation of Plant, total 57,389,846.70). The four other functions (Maintenance of Plant, Community Services, Debt Services, Other Misc) are gone, with their cached points, dPt and dLbl entries removed. The helper percentages '4'!K15:K23 now divide by SUM($D$15:$D$23) instead of D29 (e.g. Operation of Plant 32%, School Adm 24%), K24:K27 are cleared, and calcChain is updated to match. Direct XML edit, no other cell or chart changed. The LibreOffice render shows the 9-slice pie.
- other finding, major, not in findings.json: The prompt doesn't say which fund's amounts to use for the General Support Services pie; the key quietly uses the General Fund only
  - Change: grader guidance: added the task note after the opening paragraph: 'Task note: for the bottom General Support Services pie, the reference uses the General Fund amounts of the nine General Support Services items (sheet '4' column D, headed GENERAL SUPPORT SERVICES, total 57,389,846.70). The prompt does not name a fund, so also accept a pie of the same nine items built from all-funds totals (sheet '4' column J, or 'Comb Rev & Expend Page 2' J24:J32, which differ because sheet '4' hardcodes Facilities Acq. & Const. in F18), with each slice's percentage computed on that same basis.'
- other finding, minor, not in findings.json: The source's detailed table hardcodes values that don't tie to the combined statement
  - Change: Same grader-guidance task note as another finding (not listed): an all-funds pie is accepted from either sheet '4' column J or 'Comb Rev & Expend Page 2' J24:J32.
- other finding, minor, not in findings.json: Expenditure amounts disagree across same-period source tables
  - Change: Same grader-guidance task note as another finding (not listed) covers the conflicting all-funds amounts for the bottom pie.
