# Changes: FINCH task-017

Fix summary (from the fix record):

Merchant guide now states that an empty list, like null, means a fee rule applies to all values (the convention the answer key relies on).

Changed files (in this folder):

- inputs/17_src_2.md

## Fixed

- other finding, minor, not in findings.json: Graded fee matching requires an undocumented empty-list convention
  - Change: Data 17_src_2.md (merchant guide) line 95: 'If a field is set to null it means...' became 'If a field is set to null or to an empty list it means that it applies to all possible values of that field.' The GT already treats [] as unrestricted (all ten reference fee IDs have merchant_category_code: []), so the answer is unchanged.
