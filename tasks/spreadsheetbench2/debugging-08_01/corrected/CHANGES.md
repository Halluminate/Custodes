# Changes: SpreadsheetBench 2 debugging-08_01

Fix summary (from the fix record):

The prompt asks for a thorough audit, but the key fixed only the planted double counting and kept other real errors QA named. The key now also fixes them (R84 NWC link, C90 tax sign, EBT interest in C28:Q28, C36:H36 D&A links, K/L margin rows, M27/R27 denominators, period headers, Revenue Build S9:V9), recalculated with the verifier's LibreOffice. Quarterly capex I62:L62 has no defensible repair and leaves answer_position.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_08_golden.xlsx

## Fixed

- [F4](../findings.json) (Verification): Undisclosed scope constraint and unfixed defects in golden workbook ('Double Counting' only vs. 'audit and fix thoroughly')
  - Change: gt_08_golden.xlsx now also fixes the errors QA named (on top of the 20 planted double-counting cells), with every other cell, formula and style unchanged and 91 dependent cached values rewritten from the verifier's own LibreOffice recalc: 'Operating Model + DCF'!R84 =R847-M83 -> =R83-M83 (2026 change in NWC -29.61 -> -113.91, so D94/D95/D100/C102 and the DCF outputs move); C90 tax rate -0.3 -> 0.3 like D90:H90 (C91 NOPAT -169.51 -> -91.27); row 28 EBT now subtracts interest once in C28:Q28 = X20-X23-X26 (the planted N28:Q28 subtracted it twice, the old key and C28:M28 not at all; F28 now 52.554 = 'IS Annual'!F24 pretax income; R28:V28 are not named by any finding and are unchanged); C36:H36 historical D&A ='IS Annual'!C75:H75 (empty, 0) -> =CFS!E4:J4 (FY2019-FY2024 D&A 70.248 ... 78.738, matched by year; CFS C:D are FY2017-18); K9:L9, K12:L12, K15:L15 =K41/K47/K53 (empty) -> =K8/K4, =K11/K4, =K14/K4 like I:J; M27/R27 =M26/M7, =R26/R7 (COGS) -> =M26/M4, =R26/R4 (revenue); period headers: I3:J3 and I60:J60 2024 -> 2025, N3 and N60:O60 2025 -> 2026 (O3 follows N3); 'Revenue Build'!I3:J3 2023 -> 2024, N3:O3 2024 -> 2025, S3:T3 2025 -> 2026, L21 24 -> 2024; 'Revenue Build'!S9:V9 =S37 (Base row) -> =S35 (Case Selection row, same value with case 2). Quarterly capex 'Operating Model + DCF'!I62:L62 (='IS Quarters'!E69:H69, the depreciation row) has no single defensible repair because the workbook has no quarterly capex data, so I62:L62 leave answer_position (their dependents M62 and the DCF stay graded). Checked with the real SB2 scorer: new key vs itself 1.0; untouched input plus all key fixes 1.0; untouched input 0.0 (mod 0.0); planted-only fixes (the old key) now fail (mod 0.6373), as expected.
- [F3](../findings.json) (Verification): The answer key leaves pre-existing errors unfixed (e.g., broken R84 reference, negative 2025 tax rate, other non-injected errors), so the grader accepts only the four injected double-counting fixes and fails an agent that makes other legitimate fixes during the requested full audit
  - Change: Same key change (R84, C90, M27/R27 fixed; I62:L62 out of answer_position). gt_08_golden.xlsx now also fixes the errors QA named (on top of the 20 planted double-counting cells), with every other cell, formula and style unchanged and 91 dependent cached values rewritten from the verifier's own LibreOffice recalc.
- [F1](../findings.json) (Verification): Answer key removes interest entirely from pretax income
  - Change: Key 'Operating Model + DCF'!N28:Q28 =N20-N26 -> =N20-N23-N26 (interest subtracted once), and the same for C28:M28, which the finding's evidence calls broken (R28:V28 are not named and stay unchanged); dependent rows 31, 33, 34 recalculated. Part of the same key change.
- [F2](../findings.json) (Verification): Golden workbook preserves a wrong working-capital reference and penalizes its repair
  - Change: Key 'Operating Model + DCF'!R84 =R847-M83 -> =R83-M83 (-113.906); D94, D95, D100, C102, C107, C121, C135 and the other DCF outputs recalculated. Part of the same key change.
