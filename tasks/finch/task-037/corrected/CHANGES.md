# Changes: FINCH task-037

Fix summary (from the fix record):

The reference WA Price divided by the Volumes Total column, which stops at May 2006, so L60:L66 were #DIV/0!, and it used only the current month's volume in months where volume changes. The reference formulas now divide by the summed volumes over both day blocks, giving real prices for every month. Full pass: no further change.

Changed files (in this folder):

- reference/gt_37_ref_0.xlsx

## Fixed

- [F3](../findings.json) (Verification): Ground truth WA Price formula in gt_37_ref_0.xlsx is mathematically flawed at volume transition months and produces #DIV/0! errors for the last 7 months (June–December 2006)
  - Change: gt_37_ref_0.xlsx (sheet XML edited directly, rest of the file untouched): Exposure!L6:L66 WA Price now divides Total (J) by the actual volume over the exposure days, L6 =J6/SUM(Volumes!B4:H4)/25 and L{r} =J{r}/(A{r-1}*SUM(Volumes!B{r-3}:H{r-3})+25*SUM(Volumes!B{r-2}:H{r-2})), summing B:H so the blank Volumes!I58:I64 no longer give #DIV/0!. Cached values written: L60:L66 now 2.62/2.50/2.55/2.57/2.58/2.68/2.84 instead of #DIV/0!, L12 now 1.7226 instead of 2.0272 (volume change month). All other L values are unchanged because daily volume is flat in those months.
- [F2](../findings.json) (Verification): Ground truth shows #DIV/0! in WA Price for 7 months that have real exposure
  - Change: gt_37_ref_0.xlsx (sheet XML edited directly, rest of the file untouched): Exposure!L6:L66 WA Price now divides Total (J) by the actual volume over the exposure days, L6 =J6/SUM(Volumes!B4:H4)/25 and L{r} =J{r}/(A{r-1}*SUM(Volumes!B{r-3}:H{r-3})+25*SUM(Volumes!B{r-2}:H{r-2})), summing B:H so the blank Volumes!I58:I64 no longer give #DIV/0!. Cached values written: L60:L66 now 2.62/2.50/2.55/2.57/2.58/2.68/2.84 instead of #DIV/0!, L12 now 1.7226 instead of 2.0272 (volume change month). All other L values are unchanged because daily volume is flat in those months.
- [F1](../findings.json) (Environment & Infra): Incomplete seeded volume totals produce division-by-zero errors in the reference
  - Change: gt_37_ref_0.xlsx (sheet XML edited directly, rest of the file untouched): Exposure!L6:L66 WA Price now divides Total (J) by the actual volume over the exposure days, L6 =J6/SUM(Volumes!B4:H4)/25 and L{r} =J{r}/(A{r-1}*SUM(Volumes!B{r-3}:H{r-3})+25*SUM(Volumes!B{r-2}:H{r-2})), summing B:H so the blank Volumes!I58:I64 no longer give #DIV/0!. Cached values written: L60:L66 now 2.62/2.50/2.55/2.57/2.58/2.68/2.84 instead of #DIV/0!, L12 now 1.7226 instead of 2.0272 (volume change month). All other L values are unchanged because daily volume is flat in those months.
