# Changes: GDPval 90f37ff3-e4ed-4a0b-94bb-bed0f7def1ef

Fix summary (from the fix record):

The prompt now gives the subject's ZIP (33056, as in the expert file and rubric) so the 3-mile radius has an anchor, and the grader guidance tells the judge not to credit the expert file with the rubric items it misses (no comp addresses, dates or distances). Web access to LoopNet/Crexi is an environment matter. Full pass: the suite-size rubric item now follows the prompt's 2,225 SF instead of the expert PDF's 2,175 SF.

Changed files (in this folder):

- prompt.md
- grader_guidance.md

## Fixed

- [F1](../findings.json) (Environment & Infra): The subject property's location is missing
  - Change: prompt.md first sentence: 'in the Miami Gardens, FL area.' -> 'in Miami Gardens, FL 33056.' (the location the GT page 2 and the rubric's ZIP item use).
- [F3](../findings.json) (Verification): Ground truth PDF fails multiple rubric criteria and uses placeholder names instead of required street addresses
  - Change: grader_guidance.md: added one sentence after the scoring line: 'The expert deliverable lists its comparables only as Shopping Center 1 to 5, without street addresses, dates or distances, so wherever it misses a rubric item, do not credit it with that item when you compare.' The GT PDF cannot be corrected faithfully (its comps are anonymised), so the grading is fixed instead.
- [F2](../findings.json) (Verification): The expert ground truth fails many of its own rubric items, which makes the pairwise baseline weak
  - Change: Same added grader-guidance sentence (expert baseline not credited for rubric items it misses).
- other finding, major, not in findings.json: Direct contradiction on vacant suite size between problem statement (2,225 SF) and grader guidance / ground truth (2,175 SF)
  - Change: grader_guidance.md: suite-size rubric item now credits 2,225 SF, the size the prompt states, and tells the judge not to penalize the agent for differing from the expert PDF's 2,175 SF.
- other finding, major, not in findings.json: The suite size in the prompt (2,225 SF) contradicts the rubric and ground truth (2,175 SF)
  - Change: grader_guidance.md: suite-size rubric item now credits 2,225 SF, the size the prompt states, and tells the judge not to penalize the agent for differing from the expert PDF's 2,175 SF.
- other finding, major, not in findings.json: The grader requires a different suite size from the task statement
  - Change: grader_guidance.md: suite-size rubric item now credits 2,225 SF, the size the prompt states, and tells the judge not to penalize the agent for differing from the expert PDF's 2,175 SF.
