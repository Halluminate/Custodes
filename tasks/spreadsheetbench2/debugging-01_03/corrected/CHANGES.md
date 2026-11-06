# Changes: SpreadsheetBench 2 debugging-01_03

Fix summary (from the fix record):

The golden workbook's cached values were stale leftovers from the data-table substitution, so even the golden failed its own check. The caches are now refreshed from the verifier's recalculation. The four sensitivity grids, which held one flat string, are dropped from the graded range. Major/minor pass: the scenario-selector sentence in the prompt now names the M&A add-on case selector.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_01_golden.xlsx

## Fixed

- [F5](../findings.json) (Verification): Golden gate: the ground-truth deliverable does not score full reward
  - Change: gt_01_golden.xlsx: the 65 stale cached values left over from LibreOffice's data-table substitution are replaced with the base-case values from the verifier's own forced recalculation, which freezes data tables (Ex 1 - LBO C11 18.2034->14.2034, C32 109.52->101.35, F20:F28, C34, C37, U17:U54, X23:AC26; Ex 2 C3/C4/C8; Ex 5 C75/J75/Q75/X75, K79:U81). Formulas are unchanged. The patched GT scores reg 1.0 / mod 1.0 locally, where the original scored reg 0.997 / mod 0.966.
- [F6](../findings.json) (Verification): SpreadsheetBench 2 official cell check: `verify_spreadsheetbench2_cells` always fails (0.0) because `managed_recalculated_xlsx` freezes data tables on the submission while `gt_01_golden.xlsx` has un-recalculated `TABLE(...)`-corrupted cached values
  - Change: gt_01_golden.xlsx: the 65 stale cached values left over from LibreOffice's data-table substitution are replaced with the base-case values from the verifier's own forced recalculation, which freezes data tables (Ex 1 - LBO C11 18.2034->14.2034, C32 109.52->101.35, F20:F28, C34, C37, U17:U54, X23:AC26; Ex 2 C3/C4/C8; Ex 5 C75/J75/Q75/X75, K79:U81). Formulas are unchanged. The patched GT scores reg 1.0 / mod 1.0 locally, where the original scored reg 0.997 / mod 0.966. answer_position for 'Ex 1 - LBO' changed from B1:AK95 to B1:AF95, AG1:AK17, AG23:AK26, AG32:AK35, AG41:AK44, AG50:AK95. This leaves out only the four 5x5 data-table result grids (AG18:AK22, AG27:AK31, AG36:AK40, AG45:AK49). In those grids every GT cell holds the same string '2.4x/19%', and the verifier freezes data tables to the submission's own caches, so a real sensitivity table cannot match. The row/column headers and every other cell are still graded.
- [F1](../findings.json) (Verification): Corrupted ground-truth workbook (`gt_01_golden.xlsx`) contains LibreOffice Multiple Operations (`TABLE(...)`) pollution in 65 cached cells and fails its own verifier
  - Change: gt_01_golden.xlsx: the 65 stale cached values left over from LibreOffice's data-table substitution are replaced with the base-case values from the verifier's own forced recalculation, which freezes data tables (Ex 1 - LBO C11 18.2034->14.2034, C32 109.52->101.35, F20:F28, C34, C37, U17:U54, X23:AC26; Ex 2 C3/C4/C8; Ex 5 C75/J75/Q75/X75, K79:U81). Formulas are unchanged. The patched GT scores reg 1.0 / mod 1.0 locally, where the original scored reg 0.997 / mod 0.966.
- [F4](../findings.json) (Verification): The ground-truth workbook fails its own verifier: its cached values are left over from the data-table substitution
  - Change: gt_01_golden.xlsx: the 65 stale cached values left over from LibreOffice's data-table substitution are replaced with the base-case values from the verifier's own forced recalculation, which freezes data tables (Ex 1 - LBO C11 18.2034->14.2034, C32 109.52->101.35, F20:F28, C34, C37, U17:U54, X23:AC26; Ex 2 C3/C4/C8; Ex 5 C75/J75/Q75/X75, K79:U81). Formulas are unchanged. The patched GT scores reg 1.0 / mod 1.0 locally, where the original scored reg 0.997 / mod 0.966.
- [F3](../findings.json) (Verification): Every cell in the ground-truth sensitivity tables holds the same base-case string
  - Change: answer_position for 'Ex 1 - LBO' changed from B1:AK95 to B1:AF95, AG1:AK17, AG23:AK26, AG32:AK35, AG41:AK44, AG50:AK95. This leaves out only the four 5x5 data-table result grids (AG18:AK22, AG27:AK31, AG36:AK40, AG45:AK49). In those grids every GT cell holds the same string '2.4x/19%', and the verifier freezes data tables to the submission's own caches, so a real sensitivity table cannot match. The row/column headers and every other cell are still graded.
- [F2](../findings.json) (Verification): Inconsistent golden caches cause the golden workbook to fail its own verifier
  - Change: gt_01_golden.xlsx: the 65 stale cached values left over from LibreOffice's data-table substitution are replaced with the base-case values from the verifier's own forced recalculation, which freezes data tables (Ex 1 - LBO C11 18.2034->14.2034, C32 109.52->101.35, F20:F28, C34, C37, U17:U54, X23:AC26; Ex 2 C3/C4/C8; Ex 5 C75/J75/Q75/X75, K79:U81). Formulas are unchanged. The patched GT scores reg 1.0 / mod 1.0 locally, where the original scored reg 0.997 / mod 0.966.
- other finding, major, not in findings.json: Task instructions state 'The active scenario case selector value is 3' without specifying `Ex 5 - M&A!C4`, misleading agents into changing `Ex 1 - LBO!C9` from 1 to 3
  - Change: Prompt: 'The active scenario case selector value is 3.' -> 'The M&A add-on case selector value is 3.' The sentence already supplied the deleted value; it now names the selector the key restores (Ex 5's acquisitions case) instead of reading as the Operating Case. No scoring change, so no re-grade needed.
- other finding, major, not in findings.json: Scenario-selector instruction does not identify the selector that should equal 3
  - Change: Prompt: 'The active scenario case selector value is 3.' -> 'The M&A add-on case selector value is 3.' The sentence already supplied the deleted value; it now names the selector the key restores (Ex 5's acquisitions case) instead of reading as the Operating Case. No scoring change, so no re-grade needed.
