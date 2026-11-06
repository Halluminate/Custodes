# Changes: SpreadsheetBench 2 debugging-06_09

Fix summary (from the fix record):

The prompt asks for a thorough audit, but the answer key fixed only the planted reference errors and kept other real errors QA named. The key now also fixes them: Revenue Build!AC41/AC43 (=rri -> a working RRI CAGR), Supporting Schedules!K20 (hardcoded 264 -> =J20) and O76:Y76 (Base row 80 -> active-case row 77), PTA!R22 (O35:X35 -> J35:S35) and R26 (X34 -> S34). PTA!R24:R26 and their dependents R28, R32, R35, R38, R39 leave answer_position because R24 (Median EV/EBIT) has no defensible value. Cached values are the verifier's LibreOffice recalc.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_06_golden.xlsx

## Fixed

- [F1](../findings.json) (Verification): Golden workbook leaves two #NAME? errors unfixed and omits other formula bugs, while the broad prompt and binary 99.8% regression threshold penalize valid fixes
  - Change: gt_06_golden.xlsx, each named error now fixed in the key (other cells, formulas and styles unchanged, 150 dependent cached values rewritten from the verifier's LibreOffice recalc): 'Revenue Build'!AC41/AC43 =rri(5,W41,AA41) (#NAME?) -> =RRI(5,W41,AA41) / =RRI(5,W43,AA43) = 0.3797 / 0.7188; 'Supporting Schedules'!K20 hardcoded 264 -> =J20 (so K20:S20 all carry the 264.35 average instead of alternating 264 / 264.35); 'Supporting Schedules'!O76:Y76 now use the active-case utilization O77:Y77 like N76 (were Base O80:Y80); 'PTA'!R22 =SUM('Operating Model'!J35:S35) (was O35:X35, half empty) and R26 discounts by 'Operating Model'!S34 (was empty X34). 'PTA'!R25 points at the empty R24 'Median EV/EBIT Multiple', and the sheet has no EV/EBIT data to fill it (one value, and R25 multiplies revenue), so there is no single defensible repair: answer_position now leaves out PTA R24:R26 and the cells that depend on them (R28, R32, R35, R38, R39). Checked with the real SB2 scorer: new key vs itself 1.0, input plus all key fixes 1.0, untouched input 0.0, planted-only fixes (old key) 0.0 (expected).
