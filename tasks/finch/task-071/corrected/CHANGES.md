# Changes: FINCH task-071

Fix summary (from the fix record):

Full pass: the key split Arnault and Slim into two people each by name variant and broke the stated tie-break order in Sheet4; Sheet2/Sheet4 are corrected from the key's own RawData. The guidance accepts either SD convention and either rounding of a .5 median age.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_71_ref_0.xlsx

## Fixed

- other finding, major, not in findings.json: Ground-truth workbook (gt_71_ref_0.xlsx) splits the same billionaire across unnormalized name variants and violates the tie-break sorting rule in Sheet4_Ranking_Stability
  - Change: gt_71_ref_0.xlsx (XML-level, values only): 'Bernard Arnault' (2019) and 'Bernard Arnault & family', and 'Carlos Slim Helu' (2019) and 'Carlos Slim Helu & family' (2023), are now one person each. Sheet2 row 14 (2020 Arnault): Annual Change 0, 0.00%, Cumulative 0, 'Stable'. Sheet2 F49 (2023 Slim, returning after a gap like Bloomberg): Cumulative Growth 0 -> 45.31 (93/64-1). Sheet4 rebuilt from RawData with the key's own conventions (sample SD, span = last year - first year): Arnault 6 years 2019-2024, best 1, worst 4, avg 2.5, vol 1.22, Slightly Rising, Highly Stable; Slim 2 years 2019-2023, 5/8, 6.5, 2.12, Slightly Falling; rows sorted by Years on List then first appearance in RawData; old rows 19-20 cleared. Every other row unchanged.
- other finding, major, not in findings.json: Ground truth splits the same person into two entities ('Bernard Arnault' vs 'Bernard Arnault & family', 'Carlos Slim Helu' vs 'Carlos Slim Helu & family'), which corrupts Sheet2 and Sheet4
  - Change: gt_71_ref_0.xlsx (XML-level, values only): 'Bernard Arnault' (2019) and 'Bernard Arnault & family', and 'Carlos Slim Helu' (2019) and 'Carlos Slim Helu & family' (2023), are now one person each. Sheet2 row 14 (2020 Arnault): Annual Change 0, 0.00%, Cumulative 0, 'Stable'. Sheet2 F49 (2023 Slim, returning after a gap like Bloomberg): Cumulative Growth 0 -> 45.31 (93/64-1). Sheet4 rebuilt from RawData with the key's own conventions (sample SD, span = last year - first year): Arnault 6 years 2019-2024, best 1, worst 4, avg 2.5, vol 1.22, Slightly Rising, Highly Stable; Slim 2 years 2019-2023, 5/8, 6.5, 2.12, Slightly Falling; rows sorted by Years on List then first appearance in RawData; old rows 19-20 cleared. Every other row unchanged.
- other finding, major, not in findings.json: Sheet4 tie-break order in the ground truth breaks the stated 'order of first appearance in RawData' rule
  - Change: Same Sheet4 rebuild: rows now follow first appearance in RawData for ties (Musk before Ambani; Jim, Alice, Rob Walton; Arnault/Slim merged).
- other finding, major, not in findings.json: Unspecified sample vs. population standard deviation and years-span definition in Sheet4_Ranking_Stability, and half-way rounding rule for Median Age in Sheet5_Pivot_Summary
  - Change: grader_guidance.md: added one sentence after the opening paragraph: 'The instruction leaves two conventions open: Rank Volatility may use the sample or the population standard deviation (with the Stability Ratings that follow from that choice), and a median age that falls on .5 may be rounded either way, so accept either choice when it is applied consistently.'
- other finding, minor, not in findings.json: Median Age rounding for a .5 median is unspecified; the GT silently rounds 70.5 down
  - Change: grader_guidance.md: added one sentence after the opening paragraph: 'The instruction leaves two conventions open: Rank Volatility may use the sample or the population standard deviation (with the Stability Ratings that follow from that choice), and a median age that falls on .5 may be rounded either way, so accept either choice when it is applied consistently.'
