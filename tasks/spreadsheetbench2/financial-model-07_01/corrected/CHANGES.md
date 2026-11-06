# Changes: SpreadsheetBench 2 financial-model-07_01

Fix summary (from the fix record):

Recalculated the stale golden and reference workbooks (XLOOKUP caches were #NAME?) so the answer key passes its own check.

Changed files (in this folder):

- prompt.md
- reference/gt_07_RealEstate_golden.xlsx
- reference/untouched_input_07_01_RealEstate_input.xlsx

## Fixed

- [F5](../findings.json) (Verification): SpreadsheetBench 2 official cell check: Verifier trivially fails all valid solutions (and the golden file itself) because it recalculates only output_path in LibreOffice while reading stale `#NAME?`-derived cached values from gt_path
  - Change: Replaced the answer key and the reference workbook with copies force-recalculated through the verifier's own LibreOffice path, so their cached values are live (formulas unchanged); the recalculated golden now scores 1.0 against itself (regression 1.0, modification 1.0).
- [F4](../findings.json) (Verification): Golden gate: the ground-truth deliverable does not score full reward
  - Change: Replaced the answer key and the reference workbook with copies force-recalculated through the verifier's own LibreOffice path, so their cached values are live (formulas unchanged); the recalculated golden now scores 1.0 against itself (regression 1.0, modification 1.0).
- [F3](../findings.json) (Verification): Golden workbook contains stale cached values from broken `_xlfn.xlookup` cells while verifier recalculates only the agent's output in LibreOffice
  - Change: Replaced the answer key and the reference workbook with copies force-recalculated through the verifier's own LibreOffice path, so their cached values are live (formulas unchanged); the recalculated golden now scores 1.0 against itself (regression 1.0, modification 1.0).
- [F1](../findings.json) (Verification): The ground truth fails its own verifier: its cached values were computed by an engine that cannot evaluate XLOOKUP, but the agent's output is recalculated in LibreOffice
  - Change: Replaced the answer key and the reference workbook with copies force-recalculated through the verifier's own LibreOffice path, so their cached values are live (formulas unchanged); the recalculated golden now scores 1.0 against itself (regression 1.0, modification 1.0).
- [F2](../findings.json) (Verification): The golden workbook fails its own forced-recalculation grading
  - Change: Replaced the answer key and the reference workbook with copies force-recalculated through the verifier's own LibreOffice path, so their cached values are live (formulas unchanged); the recalculated golden now scores 1.0 against itself (regression 1.0, modification 1.0).
- other finding, major, not in findings.json: 'Commencement date' in the Prestige Financing instruction points to a different Inputs cell than the one the GT uses
  - Change: Prompt: "...reconstruct the Prestige Financing recognition based on the commencement date in Inputs." now reads "...based on the Start Date in Inputs." (the date the key and the input's own F70 = Inputs!D6 use), removing the clash with the separate "Project Commencement Date" cell D7.
- other finding, major, not in findings.json: Financing instructions and the expected recognition date use different date conventions
  - Change: Prompt: "...reconstruct the Prestige Financing recognition based on the commencement date in Inputs." now reads "...based on the Start Date in Inputs." (the date the key and the input's own F70 = Inputs!D6 use), removing the clash with the separate "Project Commencement Date" cell D7.
