# Changes: FINCH task-038

Fix summary (from the fix record):

The GT billed Oneok for 670 days but recorded 304 term days, which inflated its Actual Rate. The Actual Rate formula was never stated, and the GT silently corrected the shifted hurdle-rate inputs. GT H22/H39/D22 are corrected, one prompt sentence defines Actual Rate, and the guidance accepts either hurdle-rate choice.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- reference/gt_38_ref_0.xlsx

## Fixed

- other finding, major, not in findings.json: Undisclosed and non-standard 'Actual Rate' definition in ground truth (NPV at 15% divided by undiscounted total volume-days)
  - Change: prompt.md: added one sentence after the first: 'Actual Rate is the NPV of the Shipper’s annual cash flows at the 15% rate shown above the Actual Rate column, divided by Volume × Term (Days).' This matches every GT row (e.g. D14, D21).
- other finding, major, not in findings.json: Invalid ground-truth values for Oneok's 'Term (Days)' (H22), 'Actual Rate' (D22), and total 'Term (Days)' (H39)
  - Change: gt_38_ref_0.xlsx (static values, XML-level edit): H22 304→670, H39 65,839→66,205, D22 2.221576→1.007999 (= 33,767,958.41 NPV@15% / (50,000×670)). No other cell changed.
- other finding, major, not in findings.json: Ground truth uses only 304 days as Oneok's term, so its Actual Rate comes out impossibly high
  - Change: Same GT correction of H22, H39 and D22.
- other finding, major, not in findings.json: Source workbook has corrupted Hurdle Rate lookup formulas while prompt instructs agent to use each Shipper's hurdle rate as an input
  - Change: grader guidance: added the task note 'Task note: the source workbook's Hurdle Rate formulas in column C point to the wrong rows of the term table, and the reference replaces them with the matching term rates, so accept the output whether it keeps the source hurdle rates or corrects them this way, and count neither choice as an omission or an over-edit.' The hurdle rates feed no other metric, so the change only stops the column-C choice from deciding the binary grade.
- other finding, major, not in findings.json: Ground truth quietly rewrites the given hurdle-rate inputs, which contradicts 'use each Shipper's hurdle rate' and 'preserve original contents'
  - Change: grader guidance: added the task note 'Task note: the source workbook's Hurdle Rate formulas in column C point to the wrong rows of the term table, and the reference replaces them with the matching term rates, so accept the output whether it keeps the source hurdle rates or corrects them this way, and count neither choice as an omission or an over-edit.' The hurdle rates feed no other metric, so the change only stops the column-C choice from deciding the binary grade.
- other finding, major, not in findings.json: Seeded hurdle rates conflict with the reference for 19 of 24 contracts
  - Change: grader guidance: added the task note 'Task note: the source workbook's Hurdle Rate formulas in column C point to the wrong rows of the term table, and the reference replaces them with the matching term rates, so accept the output whether it keeps the source hurdle rates or corrects them this way, and count neither choice as an omission or an over-edit.' The hurdle rates feed no other metric, so the change only stops the column-C choice from deciding the binary grade.
- other finding, major, not in findings.json: Prompt leaves the output scope and the calculation conventions unstated, but grading is an all-or-nothing match to the reference
  - Change: Same added Actual Rate sentence in prompt.md. The other conventions it lists are standard readings of the sheet and were left unchanged.
