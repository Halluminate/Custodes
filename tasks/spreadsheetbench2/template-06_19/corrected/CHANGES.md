# Changes: SpreadsheetBench 2 template-06_19

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Undisclosed blank-cell constraint in Act vs Bud variance columns (G:I) and summary rows
  - Change: answer_position: 'IncomeStatement'!A2:I63 now leaves out the cells the key leaves blank where a filled value is equally reasonable: G:I on rows 9,10,13,16,19,22,25,27,29,30,32,33,36 (pre-formatted Act vs Bud cells on % / interest / PBT / tax / margin rows), plus B9, F9, E10, F10 (sequential/YoY changes that need missing Q4 2023 data). All 99 key cells stay graded. Grader guidance updated with the new ranges. Local SB2 scorer: GT 1.0; GT plus filled G27:I36 variances and N/A in B9/F9/E10/F10 FAIL under the old range (reg 0.9651) and PASS under the new one; untouched input FAIL (mod 0.0).
- other finding, major, not in findings.json: The grader expects some cells left blank, but the task never says which ones, and one wrong cell fails the whole task
  - Change: Same answer_position change as another finding (not listed).
- other finding, minor, not in findings.json: The prior-year section says Q1-Q4 2023 but has no Q4 2023 revenue
  - Change: Same answer_position change: B9, F9, E10, F10 no longer compared.
