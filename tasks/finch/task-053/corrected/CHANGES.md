# Changes: FINCH task-053

Fix summary (from the fix record):

The reference answer summed all 145 months through Dec 2012 instead of the requested Dec 2000 to Apr 2012, and it swapped the CNG and TCO volumes against the Volumes!G10/O10 headers. Recomputed every figure over rows 11-147 with column E as TCO and column M as CNG.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- reference/gt_answer.txt

## Fixed

- [F4](../findings.json) (Verification): The answer key sums Dec 2000–Dec 2012, but the prompt asks for Dec 2000 through April 2012
  - Change: gt_answer.txt and the reference block in grader guidance: totals recomputed over Volumes rows 11-147 (Dec 2000-Apr 2012, discount factor from Curves!B by Gas Market Report Date): nominal 71,901,426, discounted 52,010,139, difference 19,891,287.
- [F5](../findings.json) (Verification): Reference answer in grader guidance uses Dec 2000–Dec 2012 (145 months) instead of the requested Dec 2000–Apr 2012 (137 months)
  - Change: Same recomputation over Dec 2000-Apr 2012 (137 months), including the average daily volumes.
- [F1](../findings.json) (Verification): Grader reference uses December 2012 instead of the requested April 2012 cutoff
  - Change: Same recomputation over Dec 2000-Apr 2012.
- [F6](../findings.json) (Verification): The reference answer swaps the CNG and TCO volumes, so the comparison is backwards
  - Change: Average daily volumes relabelled per the headers: CNG (column M) 5,696, TCO (column E) 11,564, CNG - TCO = -5,869.
- [F2](../findings.json) (Verification): Reference answer swaps CNG and TCO labels relative to the column headers in 53_src_0.xlsx
  - Change: Same CNG/TCO relabel in gt_answer.txt and grader guidance.
- [F3](../findings.json) (Verification): Grader reference reverses the CNG and TCO daily-volume comparison
  - Change: Same CNG/TCO relabel in gt_answer.txt and grader guidance.
- other finding, critical, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: The ground truth graded low because the guidance reference disagreed with it and the source; the guidance reference block now equals the corrected gt_answer.txt.
- other finding, major, not in findings.json: Ambiguity in definition of Average Daily Nominal Volume (unweighted mean of monthly daily averages vs. total volume divided by total days)
  - Change: grader guidance (built on the prepared corrected guidance): added the task note 'Task note: Average Daily Nominal Volume may be computed either as the mean of the monthly daily volumes (as in the reference) or as total volume divided by total days, so accept either; the two differ by less than 0.2%.'
- other finding, major, not in findings.json: The prompt asks for a figure for each month, but the reference answer is a single aggregate total
  - Change: prompt.md: added one sentence after the first: 'Report the nominal volume, discounted volume and their difference as totals over the whole period.'
