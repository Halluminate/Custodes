# Changes: FINCH task-073

Fix summary (from the fix record):

Merchant guide now states that an empty list, like null, means a fee rule applies to all values (the convention the answer key relies on).

Changed files (in this folder):

- inputs/73_src_2.md

## Fixed

- other finding, major, not in findings.json: The answer key relies on an unstated rule that an empty list ([]) matches everything, while the manual only says that about null
  - Change: Data 73_src_2.md (merchant guide) line 95: 'If a field is set to null it means...' became 'If a field is set to null or to an empty list it means that it applies to all possible values of that field.' The answer key already treats [] as unrestricted (46 GlobalCard rules, average 0.123217, recomputed), so the answer is unchanged. Same wording as the fix for the sibling task <id>.
- other finding, major, not in findings.json: Grading depends on undocumented empty-list wildcard semantics
  - Change: Same merchant-guide sentence change (empty list = applies to all values), so the 0.123217 key follows from the stated rule.
