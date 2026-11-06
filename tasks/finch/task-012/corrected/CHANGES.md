# Changes: FINCH task-012

Fix summary (from the fix record):

Timing_Strategy!H8 gave the same Method 1 condition for Index 1 and Index 2. The Index 2 condition now says the MA is 'falling or flat', which is what the reference formulas in column T use.

Changed files (in this folder):

- reference/gt_12_ref_0.xlsx
- inputs/12_src_0.xlsx

## Fixed

- [F2](../findings.json) (Environment & Infra): Method 1 guidance in cell H8 duplicates 'rising or flat' for both Index 1 and Index 2 signals, contradicting ground-truth formulas in column T
  - Change: data/12_src_0.xlsx (and the same cell in ground_truth/gt_12_ref_0.xlsx for consistency): Timing_Strategy!H8 text 'Go Long Index 2: When the Moving Average(MA) is either rising or flat' changed to '... either falling or flat', matching GT T15 =IF(AND(E14>=E15,F15<$B$10),-1,...). Shared-string XML edit only, charts and every other cell untouched. The 'open interval' wording was left: the bias ratio is never below -0.1, so F<B10 and |F|<B10 give the same signals.
- [F3](../findings.json) (Task Spec): Method 1 rule in H8 gives the same condition for Index 1 and Index 2
  - Change: Same H8 edit as 71224100.
- [F1](../findings.json) (Task Spec): Method 1 instructions give identical conditions for holding opposite indices
  - Change: Same H8 edit as 71224100.
- other finding, minor, not in findings.json: GT unhides two sheets that the task never asks to change
  - Change: ground_truth/gt_12_ref_0.xlsx: xl/workbook.xml sets 'Benchmark Return' and 'Timing_Strategy_Return' back to state="hidden" as in the source; no other part of the file changed.
