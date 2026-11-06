# Changes: FINCH task-124

Fix summary (from the fix record):

Corrected the 22 wrong Summary cells in the reference workbook so every value comes from the monthly sheets and cells with no source data are blank. Prompt and grading are unchanged.

Changed files (in this folder):

- reference/gt_124_ref_0.xlsx

## Fixed

- [F5](../findings.json) (Verification): Ground truth reference workbook (gt_124_ref_0.xlsx) contains broken cross-sheet references, wrong-column shifts, hardcoded values absent from source sheets, and a corrupted average cell
  - Change: gt_124_ref_0.xlsx Summary: G5 and G22 (CDD with no source) blanked, G40:G42 now =+January!C5:C7, C67:E67 now =+February!E38:G38, hardcoded G16/G33/G67/G84 and G50 blanked, F50/F67/F84 'n/a' replaced by =+January!G34, =+February!H38, =+March!H40, I39 498.3 replaced by =AVERAGE(C39:G39), I50/I67/I84 now =AVERAGE(C:G). Dependent averages I5, I16, I22, I33, I41, I42 recomputed (LibreOffice recalculation).
- [F4](../findings.json) (Verification): Answer key hardcodes values that appear nowhere in the source, even though the prompt says to leave cells blank when there is no data
  - Change: Removed the unsourced hardcodes G16=15.3, G33=25.86, G67=42.3, G84=73.3 (now blank) and replaced I39=498.3 with =AVERAGE(C39:G39) (21.5).
- [F3](../findings.json) (Verification): Answer key fills CDD rows with Average Max Temp values
  - Change: Summary!G5 and G22 (CDD rows, no current-year CDD in November/December) are now blank; I5=48.375 and I22=39.875.
- [F1](../findings.json) (Verification): January 2000 temperature cells in the answer key point at the December sheet
  - Change: Summary!G40:G42 now =+January!C5, C6, C7 (67, 46, 56); I41=43.78, I42=54.58.
- [F2](../findings.json) (Verification): Reference answer uses incorrect metric, month and year mappings
  - Change: Fixed the G5/G22 CDD links, the G40:G42 December links and the C67:E67 year shift (now February!E38:G38 = 93, 22, 0; I67=28.75).
- [F6](../findings.json) (Verification): Reference requires unsupported values despite instructions to leave missing information blank
  - Change: Unsupported Midcon hardcodes blanked and 'n/a' cells replaced with source links; averages use =AVERAGE(C:G) over the filled cells.
