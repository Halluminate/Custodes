# Changes: FINCH task-126

Fix summary (from the fix record):

Replaced the answer key with the actual source workbook plus a County filter showing every Andrews County spelling. Added a grader-guidance note that accepts the literal 'Andrew' reading too.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_126_ref_0.xlsx

## Fixed

- [F3](../findings.json) (Environment & Infra): Ground-truth 'EOTT TX-NM Facilities' sheet comes from a different version of the workbook than the source the agent gets
  - Change: Rebuilt the answer key from the agent's own input file 126_src_0.xlsx. Every cell value on all three sheets is identical to the source. The only additions are an autoFilter on 'EOTT TX-NM Facilities'!A8:AH372 (the range the source's _FilterDatabase name already defines), filtered on County = 'Andrew', 'Andrew ', 'Andrews', with the other 355 data rows hidden. The old key came from a different version of the sheet (other header layout, missing B2, 316 vs 369 facility cells).
- other finding, critical, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: Rebuilt the answer key from the agent's own input file 126_src_0.xlsx. Every cell value on all three sheets is identical to the source. The only additions are an autoFilter on 'EOTT TX-NM Facilities'!A8:AH372 (the range the source's _FilterDatabase name already defines), filtered on County = 'Andrew', 'Andrew ', 'Andrews', with the other 355 data rows hidden. The old key came from a different version of the sheet (other header layout, missing B2, 316 vs 369 facility cells). With a key that matches the input, the grader no longer has to judge a mismatched reference, which is what caused the unstable 0.72/0.01/0.85 grades.
- other finding, critical, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Rebuilt the answer key from the agent's own input file 126_src_0.xlsx. Every cell value on all three sheets is identical to the source. The only additions are an autoFilter on 'EOTT TX-NM Facilities'!A8:AH372 (the range the source's _FilterDatabase name already defines), filtered on County = 'Andrew', 'Andrew ', 'Andrews', with the other 355 data rows hidden. The old key came from a different version of the sheet (other header layout, missing B2, 316 vs 369 facility cells). The new key's County filter keeps all three spellings of Andrews County (nine rows visible, not two). A grader-guidance note says this, and says the literal 'Andrew'-only reading (rows 18 and 264) and including the ditto row 296 are also accepted.
- [F2](../findings.json) (Verification): Reference filter keeps only the two misspelled 'Andrew' rows and hides the eight correctly spelled 'Andrews' County rows
  - Change: The new key's County filter keeps all three spellings of Andrews County (nine rows visible, not two). A grader-guidance note says this, and says the literal 'Andrew'-only reading (rows 18 and 264) and including the ditto row 296 are also accepted.
- [F1](../findings.json) (Environment & Infra): Target county has conflicting spellings that produce different filtered results
  - Change: The new key's County filter keeps all three spellings of Andrews County (nine rows visible, not two). A grader-guidance note says this, and says the literal 'Andrew'-only reading (rows 18 and 264) and including the ditto row 296 are also accepted.
- other finding, major, not in findings.json: Reference never creates the 'standard table' the prompt asks for
  - Change: Already covered by the prepared grader-guidance note ('Accept a table or autofilter over that list that shows these rows'). No further change.
