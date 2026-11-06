# Changes: FINCH task-094

Fix summary (from the fix record):

No change. The only finding is the shared excel_read_range tool returning stale cached values after the file was replaced; that is a tool defect, not the task.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_answer.txt

## Fixed

- other finding, minor, not in findings.json: The reference figure for the 2001 standard deviation is truncated, not rounded
  - Change: gt_answer.txt and the reference answer in graderGuidance: 'standard deviation of about 1.52' -> 'about 1.53' (sample SD 1.528).
- other finding, major, not in findings.json: Unstated sample vs. population standard deviation convention (ddof=1 vs. ddof=0) and truncated 2001 standard deviation (1.52 vs. 1.53) in reference answer
  - Change: graderGuidance: added one task note before the output instruction accepting the sample (about 1.53 / 0.59) or population (about 1.32 / 0.51) standard deviation when the conclusion is the same; reference corrected to 1.53 (see another finding (not listed)).
- other finding, major, not in findings.json: The task does not say whether to use sample or population standard deviation, and the answer key accepts only the sample figures
  - Change: Same graderGuidance task note as another finding (not listed).
- other finding, major, not in findings.json: Reference answer in grader_guidance omits the required monthly power-to-gas price ratios for Sep–Dec 2001 and Sep–Dec 2002
  - Change: graderGuidance task note (same sentence as another finding (not listed)) lists the monthly ratios the instruction asks for: about 11.16, 10.30, 8.17, 8.14 (Sep–Dec 2001) and 9.07, 8.78, 8.09, 7.80 (Sep–Dec 2002), recomputed from 94_src_0.xlsx column B / column J.
