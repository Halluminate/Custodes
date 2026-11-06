# Changes: FINCH task-015

Fix summary (from the fix record):

The reference translated the Method 1 Index 2 rule as 'rising or flat' where the source says falling or flat, and unhid two sheets. Both are corrected in the key, and a guidance task note accepts accurate alternative wording, translated or untranslated defined names, and the source's sheet order and B5 comment.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_15_ref_0.xlsx

## Fixed

- other finding, major, not in findings.json: Reference translation flips the Method 1 'long Index 2' rule (falling MA translated as 'rising')
  - Change: files/gt/gt_15_ref_0.xlsx: Timing_Strategy!H8 shared string 'Go Long Index 2: When the Moving Average(MA) is either rising or flat' -> '... either falling or flat', matching the source 向下或持平 (and the T-column formulas). Shared-string XML edit only, every other zip member byte-identical.
- other finding, major, not in findings.json: GT unhides and reorders sheets and deletes a cell comment, none of which the task asked for
  - Change: files/gt/gt_15_ref_0.xlsx xl/workbook.xml: 'Benchmark Return' and 'Timing_Strategy_Return' set back to state="hidden" as in the source (no other attribute or part changed). Sheet order and the dropped B5 comment are covered by the grader guidance: added the task note 'Task note for this problem: treat the reference as one valid English translation and pass accurate translations whose wording or sheet names differ from it. The reference leaves the defined names (净值, 基准, 多空, 时间) and the chart's references to them in Chinese: translating them too is not an over-edit, and leaving them is not an omission. The reference also moves the 择时跟踪 tab to first place and drops the source's comment on 择时跟踪!B5: keeping the source's sheet order and keeping or translating that comment are not differences.'
- other finding, major, not in findings.json: GT leaves Chinese defined names and the chart's category reference untranslated, although the task says to translate formulas and charts
  - Change: Same task note: translating the defined names and chart references is accepted, and so is leaving them as the reference does.
- other finding, minor, not in findings.json: Reference translations are inaccurate or duplicated on several metric labels
  - Change: Same task note: the reference is one valid translation, and accurate alternative wording of labels (AH25, A4, Z21, I13/K13) passes.
- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: Same task note and the H8 key fix: the judge now treats the reference as one valid translation and does not count the reference-only sheet order, comment and defined-name choices as differences.
