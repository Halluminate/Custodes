# Changes: SpreadsheetBench 2 debugging-10_02

Fix summary (from the fix record):

Full pass: the answer key also fixes the named hardcodes K57:M57 and H43 and the broken reference in D2; answer_position drops the unread B48:B50 labels and the two cells with no single correction (G43, H291) and adds the BBC F3 repair the key already made.

Changed files (in this folder):

- grader_guidance.md
- grading.json (verifier parameters)
- reference/gt_10_golden.xlsx

## Fixed

- other finding, major, not in findings.json: Generic audit prompt conflicts with strict formula-match grading on a narrow subset of workbook defects
  - Change: files/gt/gt_10_golden.xlsx: the answer key now also fixes the other real errors QA named that have one defensible correction, by XML edits: Model!K57:M57 hardcoded 0.112/0.11/0.108 -> =CHOOSE($C$2,S57,AA57,AI57), =CHOOSE($C$2,T57,AB57,AJ57), =CHOOSE($C$2,U57,AC57,AK57) (the scenario pattern of I57:J57 and K53:M53); Model!H43 0.1 -> =SUM($F43,G43) (FY26E = 1H actual + 2H, as H41, H52, H56 and the scenario P43 do; 0.1 -> 0.197); Model!D2 =CHOOSE(C2,B4,B5,B6,#REF!) -> =CHOOSE(C2,B4,B5,B6) (drops the broken reference). Cached values recomputed with the verifier's LibreOffice recalc and written only for the 701 cells whose recalculated value changed; no other formula or cell changed. Input unchanged. verifications[0].parameters.answer_position (mode formula kept; graderGuidance range list updated): 'P&L Summary'!B48:B50 (the unreferenced 'Metric Name' labels) left out, E48:E50 still graded; Model!G43 (2H26E institutional hardcode with no single correct formula) and Model!H291 (lease formula with embedded 1,200,000 / 70,748 constants, no single correction) left out; 'BBC -- Backcountry + SAIL'!F3 added (key fixes 1.35 -> =Model!E20). Real scorer: new key 1.0 vs itself; untouched input + all key changes 1.0; the same with B48:B50 left as the original labels 1.0; untouched input 0 (mod 0.0); the previous key now fails (mod 0.7059).
- other finding, major, not in findings.json: Broken lookup fix is graded on exact label text in a display column, so other correct fixes score zero
  - Change: answer_position: 'P&L Summary'!B2:T51 split into B2:T47, C48:T50, B51:T51, so the B48:B50 display labels are no longer graded and an agent that fixes only the lookup keys E48:E50 passes (checked with the real scorer: 1.0).
- other finding, major, not in findings.json: Open-ended audit prompt is graded against a hidden list of 14 cells
  - Change: Model!H291 (embedded lease constants, no single correction) left out of answer_position; the answer key fixes the other named hardcodes (see another finding (not listed)). W89/W91/W97 are Upside-case assumption inputs and stay as they are.
- other finding, minor, not in findings.json: Verifier omits a worksheet containing an intended hardcode correction
  - Change: answer_position: added 'BBC -- Backcountry + SAIL'!F3, so the key's 1.35 -> =Model!E20 repair is graded (formula mode); golden and input+key changes score 1.0, untouched input fails on it.
