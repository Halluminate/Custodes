# Changes: FINCH task-149

Fix summary (from the fix record):

FINCH report task: grader guidance gained a task note (PDF report vs the published reference chapter, judge only workbook-derivable content and one chart per sheet, any reasonable unit for Fig2.3), and the prompt's chart sentence now names the three worksheets.

Changed files (in this folder):

- prompt.md
- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The grader guidance is a generic template that refers to output.xlsx/answer.xlsx and pivot tables, which do not fit a PDF report task
  - Change: graderGuidance: task note telling the grader to read output.xlsx/answer.xlsx as the PDF report and gt_149_ref_0.pdf. Official judge text kept verbatim.
- other finding, major, not in findings.json: An open-ended report task is graded pass/fail on whether it is 'logically equivalent' to a published World Bank chapter
  - Change: Same task note: pass criteria are one chart per sheet, correct workbook values and conclusions consistent with the data and the reference's main findings; reference figures not in the workbook are not required.
- other finding, major, not in findings.json: The reference answer is a cropped page range from a published World Bank report, not an answer key written for this task
  - Change: Same task note: tells the grader the reference is a published chapter with external context not to be required.
- other finding, major, not in findings.json: Fig2.3 and Fig2.1 have no title or units, so the agent must guess the metric and could mislabel the charts
  - Change: Same task note: any reasonable unit label for Fig2.3 is accepted (Fig2.1's GDP-growth meaning is stated in its own sheet note).
- other finding, major, not in findings.json: Revenue data omit their measurement units and denominator
  - Change: Same Fig2.3 unit sentence in the task note.
- other finding, minor, not in findings.json: The prompt says 'each spreadsheet' but provides one workbook with three sheets, so the number of required charts is unclear
  - Change: problemStatement: 'For each spreadsheet provided, create at least one chart based on the data.' -> 'For each worksheet provided (Fig2.1, Fig2.2 and Fig2.3 in 149_src_0.xlsx), create at least one chart based on the data.'
