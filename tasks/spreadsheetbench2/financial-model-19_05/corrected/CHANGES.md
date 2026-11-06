# Changes: SpreadsheetBench 2 financial-model-19_05

Fix summary (from the fix record):

The answer key's DCF sensitivity grid (DCF!M8:P8, L9:P12) now keeps the same =#DIV/0! cells as the input, since the task never asks for them and forbids editing filled cells. The Total Revenue sentence now names the blank years (FY23A–FY28E) and all four segments the answer key sums. Checked locally: the patched key scores 1.0 against itself and a simulated correct answer scores 1.0. Full pass: no task change; the major/minor findings are infra, duplicates, not fixable in the task, or false positives.

Changed files (in this folder):

- prompt.md
- reference/gt_19_Transformer_golden.xlsx

## Fixed

- [F9](../findings.json) (Environment & Infra): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells fails all valid agent solutions (score 0.0) due to 24 uninstructed #DIV/0! formula cells in DCF!L9:P12 and DCF!M8:P8
  - Change: files/gt/gt_19_Transformer_golden.xlsx: DCF!M8:P8 and DCF!L9:P12 (24 cells) set to the input's formula =#DIV/0! with cached #DIV/0! (was TABLE() with values). These cells are no longer graded as modifications. Every other cell is unchanged (checked value and formula diff).
- [F8](../findings.json) (Environment & Infra): Input workbook has corrupted #DIV/0! formulas in DCF sensitivity table (DCF!L9:P12 and DCF!M8:P8) that are never mentioned in instructions, making 24 modification cells impossible to pass
  - Change: Same GT change as verifier-correctness-0 (DCF!M8:P8, L9:P12 match the input).
- [F6](../findings.json) (Task Spec): A fully correct solution scores 0: the grader requires the DCF sensitivity table, which the task never mentions and cannot be rebuilt
  - Change: Same GT change as verifier-correctness-0 (DCF!M8:P8, L9:P12 match the input).
- [F4](../findings.json) (Environment & Infra): DCF sensitivity cells are permanently broken and require prohibited edits to pass
  - Change: Same GT change as verifier-correctness-0 (DCF!M8:P8, L9:P12 match the input).
- [F7](../findings.json) (Task Spec): Revenue Drivers Total Revenue instruction specifies incorrect year range (FY25–FY30E vs golden's FY23A–FY28E) and omits the Solar & Wind Transformers segment
  - Change: Prompt: the Revenue Drivers sentence now reads 'In the Revenue Drivers sheet, calculate Total Revenue for FY23A–FY28E by summing the Solar & Wind, Distribution, Power, and Other Special Duty Transformers segments.' (was FY25–FY30E and three segments).
- [F3](../findings.json) (Verification): Instruction says to sum three revenue segments, but the GT sums four, including the largest (Solar & Wind)
  - Change: Prompt sentence now includes the Solar & Wind segment (same sentence as F7).
- [F2](../findings.json) (Task Spec): Instruction's period range for Total Revenue (FY25–FY30E) doesn't match the blank cells the GT fills (FY23A–FY28E)
  - Change: Prompt sentence now asks for FY23A–FY28E, the blank cells F30:K30 the answer key fills (same sentence as F7).
- [F5](../findings.json) (Task Spec): Revenue instructions exclude a segment that the grader requires
  - Change: Prompt sentence now includes the Solar & Wind segment (same sentence as F7).
- [F1](../findings.json) (Verification): The erased revenue range includes historical years outside the requested range
  - Change: Prompt sentence now asks for FY23A–FY28E, which covers FY23A and FY24A (same sentence as F7).
