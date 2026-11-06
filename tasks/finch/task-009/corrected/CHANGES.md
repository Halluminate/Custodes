# Changes: FINCH task-009

Changed files (in this folder):

- grader_guidance.md
- reference/gt_9_ref_0.xlsx

## Fixed

- other finding, major, not in findings.json: Ground truth Sheet4_Technology_Manufacturer contains missing and erroneous Unit Capacity (MW) and Technology Generation values that violate the prompt's extraction rules
  - Change: gt_9_ref_0.xlsx Sheet4_Technology_Manufacturer: F37 = 8 and G37 = 'Gen 4 (8-10MW)' (Saint-Brieuc), F14 = 6 (Galloper, from '6.0-154'). Guidance note: either model of mixed Walney Extension may drive its Sheet4 row.
- other finding, major, not in findings.json: Ground truth Sheet5_Operator_Portfolio miscalculates operator capacities and shares due to unsplit newline-delimited co-owners in London Array and inconsistent entity normalization
  - Change: gt_9_ref_0.xlsx: RawData G29 London Array owners now '/'-separated, and Sheet5_Operator_Portfolio A2:F16 recomputed with London Array split four ways (Ørsted 5,636.25 MW, 33.93%). Guidance note: Sheet5 judged on consistent application of the split/normalization/ranking rules to the output's own RawData, not an exact operator-list match.
- other finding, major, not in findings.json: Undisclosed and internally inconsistent Sea / Basin classification in RawData and Sheet3_Geographic_Market without a provided source dataset
  - Change: Guidance note: any consistent sea/basin labelling is accepted, and Sheet3 is judged by correct aggregation of the output's own RawData labels.
- other finding, major, not in findings.json: GT Unit Capacity ignores the model-name rule (Saint-Brieuc left blank and labelled 'Gen 1 (<4MW)' despite '8.0-167'; Galloper given 6.3 instead of 6.0 from '6.0-154')
  - Change: Same GT fix: Sheet4 F37 = 8 / G37 'Gen 4 (8-10MW)', F14 = 6.
- other finding, major, not in findings.json: GT Sheet5 gives Ørsted all 630 MW of London Array instead of splitting it equally among the four co-owners
  - Change: Same GT fix: London Array split equally, Sheet5 recomputed (Ørsted 5,636.25 MW, shares re-based).
- other finding, major, not in findings.json: GT RawData lists Vattenfall as a Hornsea One owner, so Vattenfall's #2 total in Sheet5 is wrong
  - Change: gt_9_ref_0.xlsx RawData G25 (Hornsea One) = 'Ørsted / Global Infrastructure Partners'. Sheet5 recomputed: Vattenfall 5 projects / 1,693.25 MW (rank 3), GIP 609 MW enters at rank 9, rank 15 tie at 382.25 MW resolved alphabetically (Allianz).
- other finding, major, not in findings.json: GT normalizes operator names inconsistently, so which operators make the Sheet5 top 15 is arbitrary
  - Change: Guidance note: name-variant merging beyond the Ørsted example and ties at 15th place are not defined, so Sheet5 is judged by consistent application of the rules to the output's own owners, not by the reference's exact top-15 list.
- other finding, major, not in findings.json: Sea / Basin labels have no consistent taxonomy, so the Sheet3 regional aggregation can't be reproduced
  - Change: Same guidance note on sea/basin labelling and Sheet3.
- other finding, minor, not in findings.json: GT category labels use '≥' where the prompt specifies '>='
  - Change: gt_9_ref_0.xlsx: Sheet2 G21:G23 = 'Ultra-Large (>=10MW)' and Sheet4 G21:G23, G39 = 'Next-Gen (>=10MW)', matching the prompt's labels.
- other finding, major, not in findings.json: GT RawData contains typos and leftover formatting junk
  - Change: gt_9_ref_0.xlsx RawData: G29 London Array owners '/'-separated, G24 'vattenfall' -> 'Vattenfall'; Sheet5 recomputed. Guidance note judges Sheet5 on the output's own RawData owners, so the remaining reference text leftovers do not decide the grade.
- other finding, major, not in findings.json: Reference misclassifies Saint-Brieuc's turbine technology
  - Change: Same GT fix: Sheet4 F37 = 8 / G37 'Gen 4 (8-10MW)'.
- other finding, major, not in findings.json: Reference allocates all London Array capacity to one of four owners
  - Change: Same GT fix: London Array split equally, Sheet5 recomputed.
