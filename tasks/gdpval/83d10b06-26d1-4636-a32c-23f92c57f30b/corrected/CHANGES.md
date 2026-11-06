# Changes: GDPval 83d10b06-26d1-4636-a32c-23f92c57f30b

Fix summary (from the fix record):

Prompt now points to the real Q2/Q3 columns and adds one sentence mapping the v1 entity and metric names to the names in Population v2.xlsx; rubric column letters, quarter order and division name now match the prompt and data; the expert workbook gets only mechanical fixes (A:H restored from the Population file, its variance/flag columns moved to J/K, tab 2 renamed).

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- reference/gt_Sample v2.xlsx

## Fixed

- [F8](../findings.json) (Task Spec): Task statement references v1 entity, business, and metric names absent from Population v2.xlsx, while grader guidance checks v2 names
  - Change: prompt.md: added one sentence after the criteria list mapping CB Cash Italy, CB Correspondent Banking Greece, IB Debt Markets Luxembourg, CB Trade Finance Brazil, PB EMEA UAE, Trade Finance and metrics A1/C1 to the Division / Sub-Division / Country and KRI names in Population v2.xlsx (the mapping the rubric grades).
- [F1](../findings.json) (Task Spec): The entity and metric names in the prompt don't exist in the data, and the rubric grades one fixed reading of them
  - Change: Same crosswalk sentence in prompt.md discloses the exact mapping the rubric grades.
- [F2](../findings.json) (Environment & Infra): Required entity and metric mappings are missing from agent-facing materials
  - Change: Same crosswalk sentence in prompt.md; rubric 'Corporate Banking' changed to 'Corporate Bank' in the three entity items and 'Total Clients' to 'Total clients' to match the data.
- [F6](../findings.json) (Task Spec): Task points to the wrong input columns for quarterly data
  - Change: prompt.md: '(columns H and I)' changed to '(columns H and G)' (Q2 is column H, Q3 is column G in Population v2.xlsx).
- [F10](../findings.json) (Task Spec): The column letters in the prompt don't match the Population file or the rubric
  - Change: Kept the prompt's layout (variance in J, sample flags in K); rubric items that checked variance in column I and flags in column J now check J and K; prompt Q2/Q3 column reference corrected; the expert workbook's own variance and flag columns moved to J and K (contents unchanged).
- [F9](../findings.json) (Reward): The rubric contradicts itself on column letters and on which column holds Q2 and Q3
  - Change: grader guidance: 'Columns G and H ... Q2 2024 and Q3 2024 respectively' changed to 'Q3 2024 and Q2 2024 respectively'; all variance items now use column J and all flag items use column K (consistent with the existing 'sum of 1s in column K' and 'header for column J' items).
- [F4](../findings.json) (Reward): Column letters and Q2/Q3 column order in grader_guidance contradict problem.py, Population v2.xlsx, and themselves
  - Change: Same rubric column-letter and quarter-order fixes (variance = J, flags = K, G = Q3, H = Q2) so one layout satisfies every item.
- [F7](../findings.json) (Reward): Grader reverses the quarters and contradicts the required output columns
  - Change: Same rubric fixes: quarter order matches the file headers and variance/flag columns match the prompt's J/K.
- [F3](../findings.json) (Verification): Ground-truth workbook (gt_Sample v2.xlsx) fails multiple rubric checks and corrupts 95 cells from Population v2.xlsx
  - Change: ground_truth/gt_Sample v2.xlsx, mechanical edits only: Sample!A:H restored cell-for-cell from Population v2.xlsx (95 corrupted cells: 68 Europe sub-divisions and 27 'Transactions Prohibited countries - value' KRIs back); the expert's own variance column moved I -> J and flag column J -> K unchanged (same formulas, same 65 picks), autofilter widened to A1:K1517; tab 2 renamed 'Sample Size' -> 'Sample Size Calculation' with its content unchanged. Recomputed with the verifier's LibreOffice recalc. The other rubric gaps of the expert workbook (no sample-size workings, no sample total, no Corporate Loans/Italy pick, no large-change highlight, *100 variance with 0 for Q2=0) are left as the expert made them: filling them would mean writing new answer content.
- [F5](../findings.json) (Verification): The expert GT fails many of its own rubric checks, so a pairwise comparison against it is unreliable
  - Change: Partly fixed by the mechanical edits under F3 (tab name, column layout, restored A:H). The missing workings, sample total, Corporate Loans/Italy pick and highlight are not added: cannot-fix-safely: would invent content.
