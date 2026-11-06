# Changes: FINCH task-135

Fix summary (from the fix record):

The reference charts were defective: East used the wrong season, East/West/Total were shifted 5 weeks against their dates, and Producing ran to 10/28 against the prompt's 9/23. All four GT charts now plot the 1998/99 differences from 11/5 to 9/23, and the prompt gets one sentence naming the season. Full pass: no further change; the season finding repeats F6 (prompt already names 1998/99) and the other findings sit outside the chart inputs.

Changed files (in this folder):

- prompt.md
- reference/gt_135_ref_0.xlsx

## Fixed

- other finding, critical, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: The cause of the unstable grades was the self-contradicting reference. gt_135_ref_0.xlsx chart XML only. chart5 (Prod_Yr-Yr) now plots Data!A116:A162 / G116:G162 (was through row 167, 10/28). chart6 (East_Yr-Yr) plots AH116:AH162 / R116:R162 (was Q121:Q167, the 1997/98 season and shifted 5 weeks). chart7 (West_Yr-Yr) plots AH116:AH162 / AC116:AC162 (was AC121:AC167). chart8 (Total_Yr-Yr) plots AH116:AH162 / AN116:AN162 (was AN121:AN167). All four now pair 47 dates with 47 values from 11/5 through 9/23, all in the 1998/99 column, and the numCaches are rebuilt from the Data values. A LibreOffice render of East_Yr-Yr shows 5-Nov to 23-Sep starting at 72 Bcf (R116). No cell, style or other part changed.
- other finding, critical, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: The cause of the low GT score was a reference that contradicts the prompt and itself. gt_135_ref_0.xlsx chart XML only. chart5 (Prod_Yr-Yr) now plots Data!A116:A162 / G116:G162 (was through row 167, 10/28). chart6 (East_Yr-Yr) plots AH116:AH162 / R116:R162 (was Q121:Q167, the 1997/98 season and shifted 5 weeks). chart7 (West_Yr-Yr) plots AH116:AH162 / AC116:AC162 (was AC121:AC167). chart8 (Total_Yr-Yr) plots AH116:AH162 / AN116:AN162 (was AN121:AN167). All four now pair 47 dates with 47 values from 11/5 through 9/23, all in the 1998/99 column, and the numCaches are rebuilt from the Data values. A LibreOffice render of East_Yr-Yr shows 5-Nov to 23-Sep starting at 72 Bcf (R116). No cell, style or other part changed.
- [F4](../findings.json) (Verification): Corrupted ground truth (gt_135_ref_0.xlsx) plots the wrong year column (1997/98) on East_Yr-Yr and misaligned 47-row value ranges ($121:$167 against $116:$167 categories) on East_Yr-Yr, West_Yr-Yr, and Total_Yr-Yr
  - Change: gt_135_ref_0.xlsx chart XML only. chart5 (Prod_Yr-Yr) now plots Data!A116:A162 / G116:G162 (was through row 167, 10/28). chart6 (East_Yr-Yr) plots AH116:AH162 / R116:R162 (was Q121:Q167, the 1997/98 season and shifted 5 weeks). chart7 (West_Yr-Yr) plots AH116:AH162 / AC116:AC162 (was AC121:AC167). chart8 (Total_Yr-Yr) plots AH116:AH162 / AN116:AN162 (was AN121:AN167). All four now pair 47 dates with 47 values from 11/5 through 9/23, all in the 1998/99 column, and the numCaches are rebuilt from the Data values. A LibreOffice render of East_Yr-Yr shows 5-Nov to 23-Sep starting at 72 Bcf (R116). No cell, style or other part changed.
- [F1](../findings.json) (Task Spec): Prompt instruction 'with the x-axis running through the week ending 9/23' contradicts Prod_Yr-Yr in the ground truth and stems from the 47-row truncation bug in the other three GT charts
  - Change: GT chart5 now ends at Data!A162/G162 (week ending 9/23), matching the prompt. Charts 6-8 also end at row 162.
- [F2](../findings.json) (Verification): GT East_Yr-Yr chart plots the wrong season (1997/98 vs 1996/97) while the other three charts plot 1998/99 vs 1997/98
  - Change: GT chart6 values changed from Data!Q121:Q167 (1997/98) to R116:R162 (1998/99), the same season as the other three charts.
- [F3](../findings.json) (Verification): GT East/West/Total Yr-Yr charts are misaligned by 5 weeks: values start at row 121 but category dates start at row 116
  - Change: GT charts 6-8 now pair categories AH116:AH162 with values from rows 116:162, so there is no 5-week shift.
- [F6](../findings.json) (Task Spec): Prompt's 'x-axis running through the week ending 9/23' appears to come from the misaligned GT, contradicts the GT Producing chart, and does not say which season to compare
  - Change: The GT now ends at 9/23 on all four charts. One sentence was added to the prompt after the 9/23 clause: 'Plot the 1998/99 differences (1998/99 versus 1997/98) from the year-over-year block on the Data sheet.'
- [F5](../findings.json) (Verification): Reference charts pair weekly differences with the wrong dates
  - Change: gt_135_ref_0.xlsx chart XML only. chart5 (Prod_Yr-Yr) now plots Data!A116:A162 / G116:G162 (was through row 167, 10/28). chart6 (East_Yr-Yr) plots AH116:AH162 / R116:R162 (was Q121:Q167, the 1997/98 season and shifted 5 weeks). chart7 (West_Yr-Yr) plots AH116:AH162 / AC116:AC162 (was AC121:AC167). chart8 (Total_Yr-Yr) plots AH116:AH162 / AN116:AN162 (was AN121:AN167). All four now pair 47 dates with 47 values from 11/5 through 9/23, all in the 1998/99 column, and the numCaches are rebuilt from the Data values. A LibreOffice render of East_Yr-Yr shows 5-Nov to 23-Sep starting at 72 Bcf (R116). No cell, style or other part changed.
