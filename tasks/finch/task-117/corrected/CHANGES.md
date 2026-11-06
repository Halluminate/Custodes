# Changes: FINCH task-117

Fix summary (from the fix record):

The answer key now actually uses one typeface: the nine Courier New entries are switched to Antique Olive via the style table. A guidance note says any single font family passes and size changes are optional.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_117_ref_0.xlsx

## Fixed

- other finding, critical, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Answer key: in xl/styles.xml the 8 cellXfs that used font 10 (Courier New 16 bold) now use font 15 (Antique Olive 16 bold, otherwise identical). The nine data entries A10, D10, I10, L10, O10, A12, L12, P12 and U12 are now Antique Olive like every other populated cell. Values, sizes, fills, borders, alignment, drawings and controls are unchanged. Added a grader-guidance note: typeface means font family, any single family passes, and font-size changes are optional.
- [F4](../findings.json) (Reward): AI grader (production): rejects a valid answer on "overall grade"
  - Change: Answer key: in xl/styles.xml the 8 cellXfs that used font 10 (Courier New 16 bold) now use font 15 (Antique Olive 16 bold, otherwise identical). The nine data entries A10, D10, I10, L10, O10, A12, L12, P12 and U12 are now Antique Olive like every other populated cell. Values, sizes, fills, borders, alignment, drawings and controls are unchanged. Added a grader-guidance note: typeface means font family, any single family passes, and font-size changes are optional.
- [F2](../findings.json) (Style): Prompt asks to standardize 'typeface' across 'all data entries', whereas ground truth leaves Courier New entries unchanged and only changes font size (14pt/16pt to 12pt) in rows 19–23
  - Change: Answer key: in xl/styles.xml the 8 cellXfs that used font 10 (Courier New 16 bold) now use font 15 (Antique Olive 16 bold, otherwise identical). The nine data entries A10, D10, I10, L10, O10, A12, L12, P12 and U12 are now Antique Olive like every other populated cell. Values, sizes, fills, borders, alignment, drawings and controls are unchanged. Added a grader-guidance note: typeface means font family, any single family passes, and font-size changes are optional.
- [F1](../findings.json) (Style): The answer key changes font size, not typeface, and leaves the Courier New entries untouched
  - Change: Answer key: in xl/styles.xml the 8 cellXfs that used font 10 (Courier New 16 bold) now use font 15 (Antique Olive 16 bold, otherwise identical). The nine data entries A10, D10, I10, L10, O10, A12, L12, P12 and U12 are now Antique Olive like every other populated cell. Values, sizes, fills, borders, alignment, drawings and controls are unchanged. Added a grader-guidance note: typeface means font family, any single family passes, and font-size changes are optional.
- [F3](../findings.json) (Verification): Ground-truth workbook does not perform the required font standardization
  - Change: Answer key: in xl/styles.xml the 8 cellXfs that used font 10 (Courier New 16 bold) now use font 15 (Antique Olive 16 bold, otherwise identical). The nine data entries A10, D10, I10, L10, O10, A12, L12, P12 and U12 are now Antique Olive like every other populated cell. Values, sizes, fills, borders, alignment, drawings and controls are unchanged. Added a grader-guidance note: typeface means font family, any single family passes, and font-size changes are optional.
