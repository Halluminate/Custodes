# Changes: SpreadsheetBench 2 debugging-04_02

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_04_golden.xlsx

## Fixed

- other finding, major, not in findings.json: Golden workbook preserves mixed-year working capital references and penalizes their repair
  - Change: files/gt/gt_04_golden.xlsx: 'PP&E, Debt, NWC'!C81:M83 (Inventory, AP, Accrued Expenses) now reference the same fiscal year as the header and the AR row (='Balance Sheet'!D17 ... N30 instead of C17 ... M30); cached values of those 33 cells set to the referenced Balance Sheet values, nothing else touched. Real scorer (formula mode): new key scores 1.0/1.0 against itself; untouched input fails (mod 0.0); old key (planted fixes only) now fails (mod 0.33) on the NWC cells.
- other finding, major, not in findings.json: The open-ended 'audit thoroughly' prompt conflicts with grading that only accepts a narrow set of fixes (output_scope_mismatch)
  - Change: answer_position (+ graderGuidance): the named leftovers with no single exact formula text are left ungraded: Assumptions!D3:H3 and D21:H21 (embedded +0.01/-0.02 case spreads, no defined home for the spread input) and 'Income Statement'!J52:J53 (nested IF missing '=3', fixable several ways). The NWC year mix it also names is fixed in the key (another finding (not listed)). Real scorer (formula mode): new key scores 1.0/1.0 against itself; untouched input fails (mod 0.0); old key (planted fixes only) now fails (mod 0.33) on the NWC cells.
- other finding, minor, not in findings.json: Income Statement!K20:N20 ground-truth modifications omitted from verifier answer_position
  - Change: answer_position (+ graderGuidance): added 'Income Statement'!K20:N20 so all five COGS hardcode fixes in the key are graded. Real scorer (formula mode): new key scores 1.0/1.0 against itself; untouched input fails (mod 0.0); old key (planted fixes only) now fails (mod 0.33) on the NWC cells.
- other finding, minor, not in findings.json: answer_position leaves out 4 of the 5 COGS fixes on the Income Statement (Income Statement K20:N20)
  - Change: answer_position (+ graderGuidance): added 'Income Statement'!K20:N20 so all five COGS hardcode fixes in the key are graded. Real scorer (formula mode): new key scores 1.0/1.0 against itself; untouched input fails (mod 0.0); old key (planted fixes only) now fails (mod 0.33) on the NWC cells.
- other finding, minor, not in findings.json: Grading omits four forecast COGS formulas that require correction
  - Change: answer_position (+ graderGuidance): added 'Income Statement'!K20:N20 so all five COGS hardcode fixes in the key are graded. Real scorer (formula mode): new key scores 1.0/1.0 against itself; untouched input fails (mod 0.0); old key (planted fixes only) now fails (mod 0.33) on the NWC cells.
