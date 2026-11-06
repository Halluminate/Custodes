# Changes: SpreadsheetBench 2 template-06_22

Fix summary (from the fix record):

The sheet header said '($ in millions)' while every input and the answer key work in thousands of dollars; the header now reads '($ in thousands)' in the input, the golden and the reference copy.

Changed files (in this folder):

- reference/gt_06_22_golden.xlsx
- reference/untouched_input_06_22_input.xlsx
- inputs/06_22_input.xlsx

## Fixed

- other finding, major, not in findings.json: Undisclosed unit-scaling convention in RevenueBuild: header states '($ in millions)', but ground truth stores unscaled thousands ($ in 000's) and sales per average sq ft in $000s/sq ft
  - Change: RevenueBuild!B5 unit label changed from '($ in millions)' to '($ in thousands)' in 06_22_input.xlsx, gt_06_22_golden.xlsx and untouched_input_06_22_input.xlsx (one shared-string edit each, nothing else touched). Square footage (000's) times $ per square foot is $000s, so the key's revenue figures and the label now agree. SB2 scorer: patched golden 1.0, patched input plus key formulas 1.0, patched untouched input fails (39 modification errors).
- other finding, major, not in findings.json: The '$ in millions' label contradicts the revenue the model actually computes (thousands of dollars)
  - Change: RevenueBuild!B5 unit label changed from '($ in millions)' to '($ in thousands)' in 06_22_input.xlsx, gt_06_22_golden.xlsx and untouched_input_06_22_input.xlsx (one shared-string edit each, nothing else touched). Square footage (000's) times $ per square foot is $000s, so the key's revenue figures and the label now agree. SB2 scorer: patched golden 1.0, patched input plus key formulas 1.0, patched untouched input fails (39 modification errors).
- other finding, major, not in findings.json: Golden revenue calculations are 1,000 times the stated monetary units
  - Change: RevenueBuild!B5 unit label changed from '($ in millions)' to '($ in thousands)' in 06_22_input.xlsx, gt_06_22_golden.xlsx and untouched_input_06_22_input.xlsx (one shared-string edit each, nothing else touched). Square footage (000's) times $ per square foot is $000s, so the key's revenue figures and the label now agree. SB2 scorer: patched golden 1.0, patched input plus key formulas 1.0, patched untouched input fails (39 modification errors).
