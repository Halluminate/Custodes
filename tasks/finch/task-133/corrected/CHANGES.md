# Changes: FINCH task-133

Fix summary (from the fix record):

The reference left the 2002 Plan subtotal ENA!M62 as a hardcoded 0 although the prompt asks for subtotals to calculate properly. The GT now has M62 = SUM(M57:M61) with M76 and M139 updated, and one guidance sentence covers the ambiguous 2001 Forecast cells C62:E62. Full pass: the hidden EPI Net Margin rows 12-17 now subtract Other Allocated in the key, and the guidance accepts either reading for those empty rows and for Q95:Q128 subtracting P.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_133_ref_0.xlsx

## Fixed

- [F2](../findings.json) (Verification): Ground truth workbook fails to fix the omitted =SUM(M57:M61) subtotal formula in ENA!M62 and its cascading roll-ups (M76, M139)
  - Change: gt_133_ref_0.xlsx ENA!M62: hardcoded 0 -> =SUM(M57:M61) (16.9), matching N62:Q62. Cached values of its roll-ups updated in place (formulas kept): M76 2205 -> 2221.9, M139 2211.8 -> 2228.7, so M139-N139-O139 now reconciles to Q139 1560.5. A LibreOffice recalculation of the patched GT confirms these are the only 3 cells that change. The 28 original Q95:Q128 fixes are untouched.
- [F3](../findings.json) (Verification): Reference answer leaves a broken roll-up in place (ENA row 62 'Upstream Products'), so an agent that does what the prompt asks gets marked wrong
  - Change: gt_133_ref_0.xlsx ENA!M62: hardcoded 0 -> =SUM(M57:M61) (16.9), matching N62:Q62. Cached values of its roll-ups updated in place (formulas kept): M76 2205 -> 2221.9, M139 2211.8 -> 2228.7, so M139-N139-O139 now reconciles to Q139 1560.5. A LibreOffice recalculation of the patched GT confirms these are the only 3 cells that change. The 28 original Q95:Q128 fixes are untouched. grader_guidance.md: added after the first paragraph: 'On the ENA sheet, the 2001 Forecast cells C62:E62 are typed totals with no detail in rows 57 to 61, so accept either leaving them as they are or replacing them with SUM formulas.'
- [F1](../findings.json) (Verification): Reference workbook leaves a material subtotal omission unrepaired
  - Change: gt_133_ref_0.xlsx ENA!M62: hardcoded 0 -> =SUM(M57:M61) (16.9), matching N62:Q62. Cached values of its roll-ups updated in place (formulas kept): M76 2205 -> 2221.9, M139 2211.8 -> 2228.7, so M139-N139-O139 now reconciles to Q139 1560.5. A LibreOffice recalculation of the patched GT confirms these are the only 3 cells that change. The 28 original Q95:Q128 fixes are untouched.
- other finding, major, not in findings.json: Ambiguity in whether 2002 Plan EBIT formulas in ENA column Q should include or exclude the Allocated expense column P
  - Change: grader_guidance.md: added after the C62:E62 sentence: 'On the ENA sheet, Q95:Q128 may also subtract the Allocated column P (every P value is 0).' Both M-N-O and M-N-O-P give the same values, so either reading of the 2002 Plan EBIT pattern passes.
- other finding, major, not in findings.json: The prompt never says how many errors there are or where, and the answer is graded pass/fail against a single reference
  - Change: gt_133_ref_0.xlsx EPI (hidden sheet) F12, F13, F15, F17: =Cr-Dr -> =Cr-Dr-Er and K12, K13, K15, K17: =Hr-Ir -> =Hr-Ir-Jr, matching the Net Margin definition in F9 (=C9-D9-E9) and K9. Formula text only in sheet2.xml, cached values stay 0 (rows are empty), no other cell changed (8-cell diff against the prepared GT). grader_guidance.md: added 'On the hidden EPI sheet, the reference's Net Margin formulas in F12:F17 and K12:K17 now also subtract the Other Allocated column, as F9 and K9 do, but those rows are empty, so accept either that correction or the original formulas.' The Q-without-P point is covered by the another finding (not listed) sentence. Blank ENA!P133:P136 is not an error (blank equals 0 under the official judge rules and no formula is missing).
