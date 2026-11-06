# Changes: FINCH task-018

Fix summary (from the fix record):

The answer key held -0.940000, a truncated value. Fee 384 matches 12 January 2023 Belles_cookbook_store transactions totalling 729.31 EUR, so the delta is (1-14)*729.31/10000 = -0.948103. The reference answer in gt_answer.txt and in the grader guidance now reads -0.948103. Full pass: merchant guide now states that an empty list, like null, means a fee rule applies to all values (the convention the key relies on; same wording as sibling tasks <id> and <id>).

Changed files (in this folder):

- grader_guidance.md
- reference/gt_answer.txt
- inputs/18_src_2.md

## Fixed

- [F2](../findings.json) (Verification): Ground truth answer (-0.940000) is truncated to 2 decimal places instead of rounded to 6 decimal places (-0.948103), and grader guidance lacks a numeric tolerance for this task
  - Change: gt_answer.txt changed from -0.940000 to -0.948103, and the 'Reference answer (text)' line in the grader guidance changed to match.
- [F3](../findings.json) (Verification): The reference answer -0.940000 is wrong; the correct 6-decimal answer is -0.948103
  - Change: Same fix: reference answer is now -0.948103 in gt_answer.txt and the grader guidance.
- [F1](../findings.json) (Verification): Reference answer conflicts with the supplied fee formula and transaction data
  - Change: Same fix: reference answer is now -0.948103 in gt_answer.txt and the grader guidance.
- other finding, minor, not in findings.json: Fee matching depends on undocumented empty-list wildcard semantics
  - Change: Data 18_src_2.md (merchant guide) line 95: 'If a field is set to null it means...' became 'If a field is set to null or to an empty list it means that it applies to all possible values of that field.' The key already treats [] as unrestricted, so the answer is unchanged. Same wording as sibling tasks <id> and <id>.
