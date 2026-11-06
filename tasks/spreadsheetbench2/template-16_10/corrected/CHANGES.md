# Changes: SpreadsheetBench 2 template-16_10

Fix summary (from the fix record):

The key overwrote the input's 'Margin' label in DCF!G42 with a formula the prompt never asks for; that one cell is no longer graded. Full pass: prompt now states the pro forma Actual Vacancy is zero (covered by the 5% general vacancy), and the =TODAY() cells SharedData!A3:A4 are no longer graded.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- [F1](../findings.json) (Task Spec): Undisclosed requirement to overwrite pre-populated text label 'Margin' in DCF!G42 contradicts prompt instruction not to alter existing values
  - Change: answer_position 'DCF'!B2:P46 split to leave out DCF!G42 only (nothing depends on it): 'DCF'!B2:P41,'DCF'!B42:F42,'DCF'!H42:P42,'DCF'!B43:P46. Keeping the 'Margin' label or writing the NOI margin both pass; every other cell is graded as before.
- other finding, major, not in findings.json: Unstated underwriting assumptions for Pro Forma Loss-to-Lease (DCF!H11) and Actual Vacancy & Credit Loss (DCF!H12)
  - Change: Prompt: added one sentence after the instruction: In the Pro Forma column, set Actual Vacancy & Credit Loss to zero, since vacancy is underwritten through the 5% general vacancy line. This states the key's DCF!H12 = 0 (the rent roll's actual vacancy SharedData!O12 is replaced by the 5% general vacancy in H25). Answer key unchanged.
- other finding, major, not in findings.json: TODAY() cells in the graded range use up the entire regression tolerance
  - Change: verifications[0].parameters.answer_position: 'SharedData'!A1:Q12 -> 'SharedData'!A1:Q2,'SharedData'!B3:Q4,'SharedData'!A5:Q12 (skips A3 =TODAY() and A4 'As of Date' text built from TODAY()). Grader guidance range text updated. SB2 scorer: golden with the old range 1 error (A4); with the new range regression 1.0, modification 1.0, 0 errors; untouched input fails (mod 0).
