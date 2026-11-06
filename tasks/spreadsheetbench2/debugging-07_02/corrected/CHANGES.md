# Changes: SpreadsheetBench 2 debugging-07_02

Fix summary (from the fix record):

The golden stored 8 unchanged INDEX/MATCH formulas as single-cell array formulas, so formula mode counted them as required changes that no normally saved output can match. Stored them as ordinary formulas. The input plus the 11 real fixes now scores 1.0, and the unedited input still scores 0.

Changed files (in this folder):

- reference/gt_07_golden.xlsx

## Fixed

- [F4](../findings.json) (Reward): SpreadsheetBench 2 official cell check: verify_spreadsheetbench2_cells fails to unwrap openpyxl ArrayFormula objects in formula mode, causing a guaranteed false fail on 8 unchanged INDEX/MATCH cells
  - Change: gt_07_golden.xlsx: removed t="array" and ref from the <f> of Football Field!H6, I6, H7, I7, LBO & Lenders!W28, W29, S34 and Equity Returns!D5 (same formula text and cached values). Tested: input + the 11 golden fixes scores regression 1.0 / modification 1.0 (was 0.5789 against the old key).
- [F3](../findings.json) (Reward): Spurious ArrayFormula wrappers on 8 unchanged INDEX/MATCH cells in gt_07_golden.xlsx combined with type-strict formula comparison make the task impossible to pass
  - Change: Same GT edit. The 8 cells are now regression cells.
- [F2](../findings.json) (Reward): A complete, correct fix still scores 0: the grader requires 8 unchanged INDEX/MATCH cells to be saved as legacy array (CSE) formulas
  - Change: Same GT edit.
- [F1](../findings.json) (Reward): Formula grading rejects identical formulas because of their storage representation
  - Change: Same GT edit fixes the storage-type mismatch (the finding's diagnostic copy probably kept the array attributes in the XML). Exact-text matching of commutative variants such as S28*S29 is how the official formula mode works and is left unchanged.
- other finding, major, not in findings.json: Broad prompt asks to audit and fix all formula logic errors, broken references, and naming/typo issues, while ground truth only replaces 11 embedded hardcodes and leaves genuine model bugs in regression cells
  - Change: gt_07_golden.xlsx (on top of the prepared array-formula fix), each named error fixed by the minimal in-place edit: 'DCF Model'!D85:F85 ='BS & CF'!E9/F9/G9; F22 =-E27; C57 'Automobile and Travel'. 'Equity Returns'!I57 =I56*(1+$D$12)^$D$10-I56, H82/I82 =H81.../I81*(1+$D$12)^$D$10-H81/I81; H63 =I34/SUM($I$34:$I$36); H70/I70 =RATE($D$10, 0, -$I$36, H68/I68); C70:D70, C78:D78, C86:D86 RATE(5 -> RATE($D$10 (rest of the text kept); H86/I86 =IFERROR(RATE($D$10, 0, -$I$35, H84/I84), "Negative IRR"); I40 =D10; H93 =D17; H97:H121 IPMT period A97..A121 -> F97..F121; labels B12 'Preference Rate on Equity', B28/G28 'Multiple', B49/G49 'Total Debt Outstanding'; 'Margin Analysis'!B36/B37 'Individual'. 56 cells; cached values of the 137 dependent cells refreshed from the verifier's LibreOffice recalc. Checked with the real SB2 scorer (formula mode): new key vs itself PASS (reg 1.0, mod 1.0), input plus all 67 key changes (11 planted + 56) PASS after forced recalc, untouched input FAIL (mod 0.0).
- other finding, major, not in findings.json: The golden workbook preserves material errors despite the requested thorough audit
  - Change: gt_07_golden.xlsx: 'Margin Analysis'!C25:E25 =(SUM(C22:C24)) etc. (the *1000 removed, 6,140,000 / 6,394,000 / 6,394,000, matching D11); D85:F85 and H70:I70 fixed as in another finding (not listed). Checked with the real SB2 scorer (formula mode): new key vs itself PASS (reg 1.0, mod 1.0), input plus all 67 key changes (11 planted + 56) PASS after forced recalc, untouched input FAIL (mod 0.0).
