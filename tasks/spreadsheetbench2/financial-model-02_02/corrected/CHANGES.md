# Changes: SpreadsheetBench 2 financial-model-02_02

Fix summary (from the fix record):

The instruction named the Revenue & COGS Schedule as the Volume Growth source, but that schedule has no 2019A-2022E annual growth and the key links IS,BS,CF row 37; the prompt now names the IS,BS,CF sheet. Ratios!C14 (2019A growth, no prior year, key 'N/A') is no longer compared, so a blank or 0 there no longer fails the task. Golden 1.0, golden with C14 blank 1.0 (was mod 0.9962 = fail), untouched input fails.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Volume Growth in Ratios sheet is instructed to be linked from Revenue & COGS Schedule, but Revenue & COGS Schedule lacks 2019A-2021A annual growth and the golden links to IS,BS,CF
  - Change: problemStatement: in the Instruction, 'link Volume Growth for 2019A–2025E from the Revenue & COGS Schedule' -> '... from the IS,BS,CF sheet' (the key's Ratios!D14:I14 = 'IS,BS,CF'!F37:K37, the YOY growth under Volume in KT; the schedule has only quarterly growth and FY23E-FY25E annual growth). No other prompt text changed.
- other finding, major, not in findings.json: Instruction says to link Volume Growth from the Revenue & COGS Schedule, but the ground truth links to IS,BS,CF row 37, and the schedule has no 2019A–2022E annual growth
  - Change: Same prompt change as another finding (not listed).
- other finding, major, not in findings.json: The instructed volume-growth source lacks the historical annual data
  - Change: Same prompt change as another finding (not listed).
- other finding, major, not in findings.json: The 2019A Volume Growth cell must contain an 'N/A' marker; leaving it blank fails the whole task
  - Change: verifications[0].parameters.answer_position: 'Ratios'!B1:K31 -> 'Ratios'!B1:K13,'Ratios'!B14,'Ratios'!D14:K14,'Ratios'!B15:K31 (C14, the 2019A growth with no prior year, not compared); graderGuidance range text updated to match. id/name/function/weight/mode unchanged. Real SB2 scorer: golden 1.0, golden with C14 blank 1.0 (old range: mod 0.9962, fail), untouched input mod 0.0.
