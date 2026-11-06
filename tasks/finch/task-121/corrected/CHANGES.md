# Changes: FINCH task-121

Fix summary (from the fix record):

Full pass: grader note names the required AD142 fix and accepts harmless extra Deals fixes and recalculation side effects; GT AD142 range corrected to AD121:AD131.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_121_ref_0.xlsx

## Fixed

- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: grader guidance: added a task note naming the required Deals!AD142 fix (AD121:AD131 or AD120:AD131, -2408), so the judge no longer has to guess what a complete answer is (GT graded 0.88/0.00/0.88).
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: grader guidance: added a task note naming the required Deals!AD142 fix (AD121:AD131 or AD120:AD131, -2408); same change as exploit-probe-0.
- other finding, major, not in findings.json: Prompt asks to audit the Deal Sheet and fix formula errors in the plural, but ground truth only fixes Deals!AD142 while leaving multiple other formula errors on Deals unfixed
  - Change: grader guidance task note: corrections of the other apparent Deals formula problems QA named (E:AC vs F:AC totals, F139:F193 offset, missing row formulas 128-133, DPrice range) are accepted and do not fail over_edit_avoidance. None of them has a single defensible correction (blank spacer column, empty rows, legacy price-table layout), so the answer key is not extended with them.
- other finding, major, not in findings.json: The prompt says 'formula errors' (plural) but the answer key fixes only one cell, and over-editing is scored pass/fail
  - Change: same task note as another finding (not listed): extra harmless fixes on Deals (e.g. E:AC to F:AC) no longer fail over_edit_avoidance.
- other finding, major, not in findings.json: Manual calculation mode and broken external link in Preschedule!B67 cause recalculation of 121_src_0.xlsx in LibreOffice to either leave cached values as 0/None or introduce #VALUE! errors compared to gt_121_ref_0.xlsx
  - Change: grader guidance task note: #VALUE! in Preschedule!B67/B69 from the missing '[2]Balancing' link after recalculation, or uncalculated cached values outside Deals, are not errors introduced by the agent.
- other finding, minor, not in findings.json: The ground-truth fix for Deals!AD142 overlaps the row range of AD141 and doesn't match the AE142 formula next to it
  - Change: gt_121_ref_0.xlsx Deals!AD142 formula changed from SUM(AD120:AD131) to SUM(AD121:AD131) at XML level (cached -2408 unchanged, no other part of the file touched); task note accepts either range.
- other finding, minor, not in findings.json: The ground truth contains out-of-scope changes: a hardcoded Preschedule!B67 and two empty veryHidden sheets
  - Change: grader guidance task note: the reference's static 444 in Preschedule!B67 and its empty hidden Code/Module1 sheets are save leftovers, not expected changes.
