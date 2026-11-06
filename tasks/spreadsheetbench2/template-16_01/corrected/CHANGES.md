# Changes: SpreadsheetBench 2 template-16_01

Fix summary (from the fix record):

The key's DirectCap!C42 is NOI per SF per month, but the cell is %-formatted under a 'Per Unit' header; one prompt sentence now states that basis.

Changed files (in this folder):

- prompt.md

## Fixed

- [F5](../findings.json) (Task Spec): SpreadsheetBench 2 official cell check: Verifier fails valid NOI margin in DirectCap!C42 due to conflicting cell percentage format and undisclosed ground-truth formula
  - Change: Prompt: added one sentence after the instruction: 'In column C, show Net Operating Income per SF per month, the same basis as Effective Gross Revenue in C23.' This discloses the unit the key uses in DirectCap!C42 (=(D23-D40)/($C$5*$C$6*12) = 2.0748), overriding the misleading 0.00% format and the 'Per Unit' header above it.
- [F2](../findings.json) (Task Spec): Undisclosed metric in DirectCap!C42 (NOI Per SF/Month) contradicts cell's percentage format (0.00%)
  - Change: Prompt: added one sentence after the instruction: 'In column C, show Net Operating Income per SF per month, the same basis as Effective Gross Revenue in C23.' This discloses the unit the key uses in DirectCap!C42 (=(D23-D40)/($C$5*$C$6*12) = 2.0748), overriding the misleading 0.00% format and the 'Per Unit' header above it.
- [F1](../findings.json) (Style): C42 NOI per-unit cell is pre-formatted as a percentage, but the answer key puts $/SF/month there; under all-or-nothing grading one cell decides pass or fail
  - Change: Prompt: added one sentence after the instruction: 'In column C, show Net Operating Income per SF per month, the same basis as Effective Gross Revenue in C23.' This discloses the unit the key uses in DirectCap!C42 (=(D23-D40)/($C$5*$C$6*12) = 2.0748), overriding the misleading 0.00% format and the 'Per Unit' header above it.
- [F3](../findings.json) (Task Spec): Units of the per-unit column change silently (per-unit cells next to a per-SF NOI cell), and which column-C cells to fill is never stated
  - Change: Prompt: added one sentence after the instruction: 'In column C, show Net Operating Income per SF per month, the same basis as Effective Gross Revenue in C23.' This discloses the unit the key uses in DirectCap!C42 (=(D23-D40)/($C$5*$C$6*12) = 2.0748), overriding the misleading 0.00% format and the 'Per Unit' header above it.
- [F4](../findings.json) (Task Spec): NOI cell is formatted as a percentage but graded as dollars per square foot per month
  - Change: Prompt: added one sentence after the instruction: 'In column C, show Net Operating Income per SF per month, the same basis as Effective Gross Revenue in C23.' This discloses the unit the key uses in DirectCap!C42 (=(D23-D40)/($C$5*$C$6*12) = 2.0748), overriding the misleading 0.00% format and the 'Per Unit' header above it.
