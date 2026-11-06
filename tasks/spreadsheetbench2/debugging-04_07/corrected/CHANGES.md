# Changes: SpreadsheetBench 2 debugging-04_07

Fix summary (from the fix record):

The answer key now also fixes the extra errors QA named: interest one year late (IS J26:N26 and the debt-summary headers PP&E D65:H66), mixed-year working capital (PP&E C81:M83) and DCF C29 minority interest taken from comprehensive income (now 0). The unusual-item projections IS J29:J33 have no single repair and are no longer graded. Real SB2 scorer: new golden 1.0; input + every key change 1.0; input + only the planted sign fixes 0.0 (mod 0.4448); untouched input 0.0.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_04_golden.xlsx

## Fixed

- other finding, major, not in findings.json: Golden answer preserves mixed-year working-capital references
  - Change: files/gt/gt_04_golden.xlsx (XML-level, cached values from the verifier's LibreOffice recalc, 351 dependent cached values moved, no other formula changed): 'Income Statement'!J26:N26 =-'PP&E, Debt, NWC'!E73..I73 -> D73..H73 (same-year interest; N26 no longer 0); 'PP&E, Debt, NWC'!D65:H66 ='Income Statement'!I..M rows 11/12 -> J..N (headers 2021-2025 like D73:H73); 'PP&E, Debt, NWC'!C81:M83 ='Balance Sheet'!C..M rows 17/29/30 -> D..N (same year as C79 headers and C80 receivables; DCF C19 22.31 -> -21.65); 'DCF'!C29 =-'Balance Sheet'!I55 (comprehensive income) -> 0 (the balance sheet has no minority-interest line). Same repairs as the key of sibling task <id> on this model. answer_position drops 'Income Statement'!J29:J33. Real SB2 scorer: new golden 1.0; input + every key change 1.0; input + only the planted sign fixes 0.0 (mod 0.4448); untouched input 0.0.
- other finding, major, not in findings.json: Golden answer retains shifted interest links and zero interest on outstanding debt
  - Change: files/gt/gt_04_golden.xlsx (XML-level, cached values from the verifier's LibreOffice recalc, 351 dependent cached values moved, no other formula changed): 'Income Statement'!J26:N26 =-'PP&E, Debt, NWC'!E73..I73 -> D73..H73 (same-year interest; N26 no longer 0); 'PP&E, Debt, NWC'!D65:H66 ='Income Statement'!I..M rows 11/12 -> J..N (headers 2021-2025 like D73:H73); 'PP&E, Debt, NWC'!C81:M83 ='Balance Sheet'!C..M rows 17/29/30 -> D..N (same year as C79 headers and C80 receivables; DCF C19 22.31 -> -21.65); 'DCF'!C29 =-'Balance Sheet'!I55 (comprehensive income) -> 0 (the balance sheet has no minority-interest line). Same repairs as the key of sibling task <id> on this model. answer_position drops 'Income Statement'!J29:J33. Real SB2 scorer: new golden 1.0; input + every key change 1.0; input + only the planted sign fixes 0.0 (mod 0.4448); untouched input 0.0.
- other finding, major, not in findings.json: Open-ended 'audit thoroughly' task is graded all-or-nothing against one golden file that leaves other plausible defects unfixed
  - Change: (d) DCF C29 set to 0 in the key (see another finding (not listed) entry). (a) 'Income Statement'!J29:J33 left out of answer_position (B2:J57 split into B2:J28, B29:I33, B34:J57): projecting 0 or the latest year are both defensible, so there is no single correction. (b)/(c) need no change: one-cell label fixes pass the 0.998 regression ratio.
