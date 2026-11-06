# Changes: SpreadsheetBench 2 template-16_11

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: Ground truth fills $/Unit for only some expense rows, so filling the rest fails the pass/fail grade
  - Change: answer_position split so DCF!D36:D37 and D41 ($/Unit for Property Taxes, Insurance and NOI, blank in the key under the $/Unit header) are not graded; all other cells unchanged. graderGuidance range text updated. Scorer: key 1.0 under new range; key plus D36/D37/D41 =C/C5 and RentRoll!D11 =E11/C11 now 1.0 (fails under old range); untouched input fails.
- other finding, minor, not in findings.json: Seeded average unit size is incorrect and protected by grading
  - Change: Same answer_position change also drops RentRoll!D11 (seed =SUM(D7:D10) sum of averages), so an agent that repairs it to the weighted average is no longer failed; leaving it also passes.
- other finding, minor, not in findings.json: Seed 'Totals / Averages' row sums the per-floorplan average SF, which invites a wrong Average Unit Size
  - Change: Same answer_position change (RentRoll!D11 no longer graded). Key C6 = 883.90625 (weighted) is correct and unchanged.
