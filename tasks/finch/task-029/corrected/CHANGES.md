# Changes: FINCH task-029

Fix summary (from the fix record):

Fixed the 10x Power Risk typo in the answer key (Master M44 200,000 to 20,000, linked to the department sheet) and the grand total it feeds. Full pass: grader note accepts removing the two departments with no tab and either header/department row placement; GT headcount edits outside the task reverted.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_29_ref_0.xlsx

## Fixed

- [F2](../findings.json) (Verification): Ground truth contains a 10x typo on Power Risk budget (200,000 instead of 20,000), inflating the Master total by 180,000
  - Change: Answer key: Master!M44 (Power Risk) is now ='Power Risk East and West'!$E$16 (20,000, linked like the other departments) instead of the typed 200000. The cached grand total Master!M69 =SUM(M3:M68) is now 13,081,750. No other cell changed.
- [F1](../findings.json) (Verification): Ground truth puts Power Risk at 200,000, but the department's sheet sums to 20,000
  - Change: Answer key: Master!M44 (Power Risk) is now ='Power Risk East and West'!$E$16 (20,000, linked like the other departments) instead of the typed 200000. The cached grand total Master!M69 =SUM(M3:M68) is now 13,081,750. No other cell changed.
- [F3](../findings.json) (Verification): Reference answer overstates Power Risk budget by 180,000
  - Change: Answer key: Master!M44 (Power Risk) is now ='Power Risk East and West'!$E$16 (20,000, linked like the other departments) instead of the typed 200000. The cached grand total Master!M69 =SUM(M3:M68) is now 13,081,750. No other cell changed.
- other finding, major, not in findings.json: Contradiction between prompt instruction to remove non-existent departments and ground truth preserving all rows, combined with inconsistent row placement in Master column M
  - Change: grader guidance task note: keeping Transaction Support/SAP at 0 or removing those rows are both accepted, and Portland/Canada budgets may sit on the header row or the department row(s) with the same total.
- other finding, major, not in findings.json: Ground truth keeps rows the prompt says to remove (departments with no sheet)
  - Change: same task note as another finding (not listed): deleting the two rows with no tab, as the prompt says, is accepted alongside the reference's 0 rows.
- other finding, minor, not in findings.json: Ground truth puts some budgets on the region header row, not the department line
  - Change: same task note: Portland in M12 or M13, Canada in M17 or split across M18:M21, if the grand total is unchanged.
- other finding, minor, not in findings.json: Ground truth changes source headcount cells the task never asked about
  - Change: gt_29_ref_0.xlsx restored to the source headcounts at XML level: Fundys!E17 9->8, Fundys!E28 formula =E8+E17+E20+E24+E26 -> constant 24 (its calcChain entry removed), IT!C6 2->1. No dependent cached values change (IT!C150 does not use C6, E28 stays 24). Master and all budget cells untouched.
