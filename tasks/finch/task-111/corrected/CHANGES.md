# Changes: FINCH task-111

Fix summary (from the fix record):

The reference silently dropped the fuel adjustment from the SCG spread on the first sheet only; it is restored to the source formula and the totals recalculated.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_111_ref_0.xlsx

## Fixed

- [F3](../findings.json) (Verification): Ground truth modifies SCG spread formula on the first sheet but not on Sheet1, introducing an undisclosed and inconsistent modeling change
  - Change: gt_111_ref_0.xlsx, sheet 'March01 GDAs': restored the SCG spread I10:I40 to the source form '=+D10-F10-G10' (fuel-adjusted TW price, the shared formula the reference had rewritten to '=+D10-E10-G10'); cached values of I10:I40, N10:Q40, row 41 totals and the summary Q46/Q49 recalculated (O41 1,038,237.35 -> 1,029,836.34). Now both sheets apply the new 0.96 fuel factor to SCG, consistent with Sheet1 I10 '=+D10-(F10+G10)'. No other formula changed.
- [F1](../findings.json) (Verification): The answer key applies the new fuel factor to SCG differently on its two sheets, so whatever the agent does on one sheet will contradict the key
  - Change: gt_111_ref_0.xlsx, sheet 'March01 GDAs': restored the SCG spread I10:I40 to the source form '=+D10-F10-G10' (fuel-adjusted TW price, the shared formula the reference had rewritten to '=+D10-E10-G10'); cached values of I10:I40, N10:Q40, row 41 totals and the summary Q46/Q49 recalculated (O41 1,038,237.35 -> 1,029,836.34). Now both sheets apply the new 0.96 fuel factor to SCG, consistent with Sheet1 I10 '=+D10-(F10+G10)'. No other formula changed.
- [F2](../findings.json) (Verification): Reference silently removes SCG fuel adjustment on one worksheet
  - Change: gt_111_ref_0.xlsx, sheet 'March01 GDAs': restored the SCG spread I10:I40 to the source form '=+D10-F10-G10' (fuel-adjusted TW price, the shared formula the reference had rewritten to '=+D10-E10-G10'); cached values of I10:I40, N10:Q40, row 41 totals and the summary Q46/Q49 recalculated (O41 1,038,237.35 -> 1,029,836.34). Now both sheets apply the new 0.96 fuel factor to SCG, consistent with Sheet1 I10 '=+D10-(F10+G10)'. No other formula changed.
- other finding, minor, not in findings.json: Ground truth renames worksheet 'March'01 GDAs' to 'March01 GDAs' in contradiction to the instruction to preserve original sheets
  - Change: files/gt/gt_111_ref_0.xlsx (built on the critical-pass key): first sheet renamed back from 'March01 GDAs' to the source name "March'01 GDAs" (xl/workbook.xml sheet name and the docProps/app.xml title only; no formula or defined name refers to it). No cell changed; LibreOffice opens and recalculates it with the source name.
- other finding, major, not in findings.json: Prompt is unclear on what the 'TW→PGE fuel loss factor' covers, because the source has one shared fuel-adjusted price for both PGE and SCG
  - Change: grader_guidance.md: added a task note after the opening paragraph explaining the shared fuel-adjusted price, that the reference applies 4.0% to both spreads, and accepting 4.0% on PGE only with SCG kept at 5% when the totals follow consistently.
- other finding, minor, not in findings.json: The GT renamed the original sheet, removing the apostrophe, even though the prompt says to keep all original sheets
  - Change: files/gt/gt_111_ref_0.xlsx (built on the critical-pass key): first sheet renamed back from 'March01 GDAs' to the source name "March'01 GDAs" (xl/workbook.xml sheet name and the docProps/app.xml title only; no formula or defined name refers to it). No cell changed; LibreOffice opens and recalculates it with the source name.
