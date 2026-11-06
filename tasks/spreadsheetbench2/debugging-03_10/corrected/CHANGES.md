# Changes: SpreadsheetBench 2 debugging-03_10

Changed files (in this folder):

- reference/gt_03_golden.xlsx

## Fixed

- other finding, major, not in findings.json: Answer key violates the workbook’s explicit interest-deduction cap
  - Change: gt_03_golden.xlsx (XML edits, dependents recached from the verifier's LibreOffice recalc, nothing else changed): LBO!J37:M37 =+J36*-J20 -> =+MIN(-J36,30%*J13)*J20 (cap at 30% of EBITDA, 2018-2021) and N37 -> =+MIN(-N36,30%*N17)*N20 (30% of EBIT from 2022), per 'Ex 10 - Forecast Assumptions '!B45:B46; the cap binds every year, so the carryforward is never used. J37 31.045 -> 22.0579; dependents recached: J39:N39, revolver/TLB rows 42-56, J69:N70, K36:N36, R14:V14, R16:V16, R19:V20, Valuation Bridge C6/C8 (V16 2082.99 -> 2050.27). Scorer: new key 1.0 vs itself; previous key (planted fixes only) now fails; untouched input fails.
- other finding, minor, not in findings.json: Ground-truth model still has an obviously wrong Multiple Expansion formula and a typo (ungraded because their values do not change)
  - Change: gt_03_golden.xlsx: LBO!H31 '(S in millions)' -> '($ in millions)' (shared string used only there, matching H10/P10), and Valuation Bridge C7 =(LBO!V12-LBO!C25) -> =(LBO!V12-LBO!C25)*LBO!N13 (multiple change times exit EBITDA, mirroring C5's entry-multiple x EBITDA growth); C7 value stays 0.
