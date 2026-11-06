# Changes: GDPval 4de6a529-4f61-41a1-b2dc-64951ba03457

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: A red-team agent scored 52% of the reward without doing the real work (AI-grader stand-in)
  - Change: Grader guidance: added a grading note that the UW/N/OW/Change/Conviction/Description column items count only when those columns are filled in per line item, not with empty or uniform placeholders.
- other finding, major, not in findings.json: Mismatched and missing sub-asset class rows between input PDF and grader_guidance rubric
  - Change: Grader guidance note: row/column titles are matched by meaning, with the PDF labels listed as equivalents; the Corporate High Yield item is awarded when every PDF fixed income line is covered.
- other finding, major, not in findings.json: Undisclosed structural and legend requirements in grader_guidance not stated in prompt or reference PDF
  - Change: Grader guidance note: section/category labels laid out as the prompt describes count for the "Asset Class" and "Opportunity Set" column items. Legend item unchanged.
- other finding, major, not in findings.json: Missing coverage for populated per-row views (UW/N/OW), conviction levels, change indicators, and per-row one-sentence descriptions
  - Change: Same grading note: the column items require the columns to be filled in for the line items.
- other finding, major, not in findings.json: Rubric row labels differ from the input PDF's labels, so an agent that copies the source faithfully loses points
  - Change: Same grading note on matching titles by meaning with the PDF labels as equivalents.
- other finding, major, not in findings.json: Rubric gives no weight to the analysis and 25% of the score for repeating macro phrases the prompt supplies
  - Change: Same grading note requiring populated view/conviction/description columns; macro-phrase items left as written by the author.
- other finding, minor, not in findings.json: Grader requires a high-yield category absent from the supplied opportunity sets
  - Change: Grader guidance note: the Corporate High Yield item is awarded when the deliverable covers every fixed income line the PDF lists.
- other finding, major, not in findings.json: Rubric checks allocation-table headings but not the allocation decisions
  - Change: Same grading note requiring populated allocation columns.
