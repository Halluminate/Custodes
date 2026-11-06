# Changes: SpreadsheetBench 2 visualization-task-134

Fix summary (from the fix record):

Point E was never defined and the 'six axis crossings' wording was impossible; the prompt now names the four axis crossings and defines E as the key places it. The chart checklist had E's x off by 200,000 and an empty 18th item; both corrected. The earlier one-page chart-scaling findings remain infra.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- grading.json (verifier parameters)

## Fixed

- other finding, major, not in findings.json: The instruction asks for six axis-crossing vertices, but an ellipse crosses the axes only four times, and point E is never defined
  - Change: prompt.md: 'Label the six vertices where the ellipse crosses the axes as A, B, C, D, E, and F, proceeding clockwise from the top (A is where the ellipse crosses the positive Y-axis).' -> 'Label six vertices as A, B, C, D, E, and F, proceeding clockwise from the top (A, C, D and F are where the ellipse crosses the positive Y-axis, positive X-axis, negative Y-axis and negative X-axis).' and one added sentence after the B sentence: 'Point E is the lower-left corner formed by the x-value of F and the y-value of D, at approximately (-2,434,619, -13,413).' (the key's Z16 =+Z17, AA16 =+AA12).
- other finding, major, not in findings.json: Location of vertex E is not defined in the task instructions and contradicts the ellipse geometry in ground truth and checklist
  - Change: Same prompt sentence defining E (lower-left corner from F's x and D's y, about (-2,434,619, -13,413)), and checklist item 13 'x=-2,234,619' -> 'x=-2,434,619' (verifications[0].parameters.checklist; id/name/function/weight unchanged; graderGuidance list updated).
- other finding, major, not in findings.json: Point E's graded coordinate disagrees with the reference fixture
  - Change: Same prompt sentence defining E (lower-left corner from F's x and D's y, about (-2,434,619, -13,413)), and checklist item 13 'x=-2,234,619' -> 'x=-2,434,619' (verifications[0].parameters.checklist; id/name/function/weight unchanged; graderGuidance list updated).
- other finding, major, not in findings.json: The checklist gives the wrong x-coordinate for E and contains an empty item, so a correct chart can fail
  - Change: verifications[0].parameters.checklist: item 13 'x=-2,234,619' -> 'x=-2,434,619'; the empty 18th item '' removed (17 items, pass still needs > 0.7). graderGuidance checklist text updated to match.
- other finding, major, not in findings.json: Checklist in spec.yaml contains a trailing empty string item (item 18) that cannot be satisfied
  - Change: verifications[0].parameters.checklist: the empty 18th item '' removed; graderGuidance list updated.
- other finding, major, not in findings.json: An empty checklist item contributes to the pass threshold
  - Change: verifications[0].parameters.checklist: the empty 18th item '' removed; graderGuidance list updated.

## Confirmed findings not fixed

- [F2](../findings.json): SpreadsheetBench 2 official chart checklist: Chart renderer shrinks worksheet with 483 rows into an unreadable thumbnail and blank second page
  - Reason: infra
- [F1](../findings.json): Grader shrinks the chart until its labels are unreadable
  - Reason: infra
